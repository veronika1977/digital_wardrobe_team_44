# ADR-002: Rembg for Background Removal

## Status

Accepted

## Context

The Digital Wardrobe app requires automatic background removal from clothing photos to provide a clean, professional appearance. The team evaluated the following options:

- **Rembg (open-source, Python):** CPU-based background removal using U2-Net model
- **Remove.bg API:** Cloud-based service with high-quality results, but need to paid
- **Custom ML model:** Train own model, but requires significant data and compute resources
- **OpenCV with manual masking:** Free, but requires user intervention and produces inconsistent results

**Constraints:**

- Must process images within 5 seconds (user experience requirement)
- Must handle failures gracefully (QR-002: fault tolerance)
- Must work without external API dependencies (cost and privacy concerns)

## Decision

The team selected **Rembg** (CPU version) for background removal.

**Technology stack:**
- **Background removal library:** `rembg[cpu]` (Python package)
- **Underlying model:** U2-Net (deep learning model for salient object detection)
- **Image processing:** `Pillow` (PIL) for image loading and manipulation
- **HEIC support:** `pillow-heif` for iOS photos (converted to PNG before processing)
- **Model storage:** Pre-downloaded during Docker build to `~/.u2net/u2net.onnx`
- **Model size:** ~170 MB (U2-Net full model)
- **Processing time:** 3-5 seconds per standard image (1080p)
- **Memory usage:** ~500 MB RAM per concurrent request

**Rationale:**
1. **Cost-effective:** Open-source and free, no per-image charges (unlike Remove.bg at $0.05/image)
2. **Privacy:** All processing happens on our servers, no external API calls with user data
3. **Quality:** U2-Net model provides 85-90% accuracy for clothing items on plain backgrounds
4. **Simplicity:** Single Python package, 3 lines of code to integrate with FastAPI
5. **Fault tolerance:** If Rembg fails, we fall back to the original image (QR-002)
6. **CPU-only:** Works on standard servers without GPU, reducing infrastructure costs
7. **HEIC support:** Combined with `pillow-heif`, handles iOS photos without manual conversion

## Consequences

### Positive

- **Zero cost:** No per-image fees, unlimited processing
- **Data privacy:** User photos never leave our infrastructure
- **Offline capable:** Works without internet connection to external services
- **Controllable:** Can adjust processing parameters and fallback behavior

### Negative

- **Model size:** Rembg model is ~170MB, increases Docker image size
- **Quality limitations:** Struggles with complex backgrounds or similar foreground/background colors
- **Memory usage:** Processing requires ~500MB RAM per concurrent request

### Neutral

- **Pre-downloading:** Model must be pre-downloaded during Docker build to avoid runtime delays
- **File validation:** Strict JPEG/PNG validation required to prevent processing errors

## Related Quality Requirements

- **QR-002 (Fault Tolerance):** Rembg failures preserve original photo, ensuring 100% data preservation
- **QR-001 (Time Behaviour):** Processing time < 5 seconds for standard images

## Related Documentation
- [docs/quality-requirements.md](../../quality-requirements.md)
- [docs/architecture/README.md](../README.md)
- [CHANGELOG.md](../../../CHANGELOG.md) — US-08 implementation

---

**Date:** 2026-06-29  