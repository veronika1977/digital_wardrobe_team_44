# AI Background Removal — Rembg Integration

This document describes the selected solution for automatic background removal in Digital Wardrobe and provides integration instructions for the backend.

## 1. Selected Solution: Rembg

**Library:** [rembg](https://github.com/danielgatis/rembg)  
**Model:** U2-Net (open-source, MIT License)  
**Language:** Python  
**License:** MIT (free for commercial use)

### Why Rembg?

1. **Free and open-source** — no API keys, no subscription, no rate limits
2. **Runs locally** — photos never leave our server (better privacy)
3. **No external dependencies** — works offline, no third-party API downtime
4. **Good quality** — U2-Net model provides high-quality background removal for clothing items
5. **Easy integration** — simple Python API, 3 lines of code
6. **Suitable for MVP v1** — perfect for testing and demo without costs

### Alternatives Considered

| Service | Why Not Selected |
|---------|------------------|
| remove.bg | Paid ($0.20/image), rate limits, photos sent to external server |
| ClipDrop | Paid, rate limits, requires API key |
| Photoroom | Paid, rate limits, requires API key |

---

## 2. Technical Details

### Installation

```python
pip install rembg[cpu]  # CPU version (default)
# OR
pip install rembg[gpu]  # GPU version (faster, requires CUDA)
```

### Dependencies:

- Python 3.8+
- ONNX Runtime (auto-installed)
- Pillow (auto-installed)
- ~170 MB for U2-Net model (downloaded on first use)

### Supported Formats

Input: PNG, JPG, WEBP (any format supported by Pillow)
Output: PNG with transparent background
Max size: No hard limit, but 10 MB recommended

### Performance

For CPU (laptop):  
- 1-2 sec/image processing time
- ~500 MB memory usage

For CPU(server):  
- 0.5-1 sec/image processing time
- ~500 MB memory usage

For GPU(CUDA):  
- 0.1-0.3 sec/image processing time
- ~1 GB VRAM memory usage

## 3. Integration Instructions for Backend

### Basic Usage

```python
from rembg import remove
from PIL import Image
import io

def remove_background(input_bytes: bytes) -> bytes:
    """
    Remove background from an image using Rembg.
    
    Args:
        input_bytes: Raw image bytes (PNG, JPG, or WEBP)
    
    Returns:
        PNG image bytes with transparent background
    """
    output_bytes = remove(input_bytes)
    return output_bytes
```
### FastAPI Endpoint Example

```python
from fastapi import FastAPI, UploadFile, File, HTTPException
from rembg import remove
import io

app = FastAPI()

@app.post("/api/items/remove-background")
async def remove_background_endpoint(file: UploadFile = File(...)):
    """
    Remove background from uploaded image.
    """
    # Validate file type
    if file.content_type not in ["image/jpeg", "image/png", "image/webp"]:
        raise HTTPException(
            status_code=400,
            detail="Invalid file type. Supported: JPEG, PNG, WEBP"
        )
    
    # Validate file size (max 10 MB)
    contents = await file.read()
    if len(contents) > 10 * 1024 * 1024:
        raise HTTPException(
            status_code=400,
            detail="File too large. Max size: 10 MB"
        )
    
    try:
        # Remove background
        output_bytes = remove(contents)
        
        return {
            "filename": f"no_bg_{file.filename}",
            "content_type": "image/png",
            "data": output_bytes
        }
    except Exception as e:
        raise HTTPException(
            status_code=500,
            detail=f"Background removal failed: {str(e)}"
        )
```

###  Integration with Add Item Flow

```python
from rembg import remove
from PIL import Image
import io

async def process_item_photo(image_bytes: bytes, remove_bg: bool = True) -> bytes:
    """
    Process uploaded item photo: optionally remove background and optimize.
    
    Args:
        image_bytes: Raw uploaded image bytes
        remove_bg: Whether to remove background (default: True)
    
    Returns:
        Processed image bytes (PNG if bg removed, else original format)
    """
    if remove_bg:
        try:
            # Remove background
            image_bytes = remove(image_bytes)
        except Exception as e:
            # Fallback: return original image
            logger.warning(f"Background removal failed: {e}. Using original image.")
    
    # Optional: resize to max 1024x1024 for storage optimization
    img = Image.open(io.BytesIO(image_bytes))
    if max(img.size) > 1024:
        img.thumbnail((1024, 1024))
        buffer = io.BytesIO()
        img.save(buffer, format="PNG", optimize=True)
        image_bytes = buffer.getvalue()
    
    return image_bytes
```
## 4.  Fallback Strategy

### When Background Removal Fails

Possible failure scenarios:
- Corrupted image file
- Unsupported format
- Out of memory (very large images)
- Model loading issues (first run). 

If background removal fails (corrupted image, OOM, model issues), return the original photo:  

```python
def remove_background_with_fallback(image_bytes: bytes) -> bytes:
    try:
        return remove(image_bytes)
    except Exception as e:
        logger.warning(f"Background removal failed: {e}. Using original image.")
        return image_bytes
```

### User experience:

- Success: item with background removed  
- Failure: original photo + notification: "Background removal unavailable. Item saved with original photo."

## References

- [Rembg GitHub](https://github.com/danielgatis/rembg) 
- [U2-Net Paper](https://arxiv.org/abs/2005.09007)

**Last updated:** June 18, 2026 
**Author:** @veronika1977 
**Reviewer:** @Evgeni1a 
