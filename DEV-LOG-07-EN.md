**Dev Log #07 — Character colors and fur details**

The latest feedback says scene saving/loading now appears fixed. This update keeps that repair and focuses on colors.

Maya and Kokoa use a shader with separate surface and shade colors. The previous editor did not update all of those paths, so changes could appear mostly around the outline. The color application now handles those shader properties, including Absolute color mode.

For Maya and Kokoa, ear color now targets the outer fur while preserving the inner fluff/skin. Tail color changes the base while retaining the original tip and ornaments. Follow hair color and scene loading use the same protection.

This protection is currently mapped for those two characters only. Other characters need individual checks.

In-game rendering, protected pixels, reset, save/load and regression checks are covered. Please still check the result in HMD; lighting continues to affect the final appearance.

https://github.com/CrouchingWriter/MeltySave
