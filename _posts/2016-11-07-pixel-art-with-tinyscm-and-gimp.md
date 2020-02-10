---
layout: page
title: PixelArt with TinySCM and Gimp
---

Sometimes it is easier to generate art assets for your projects. Especially
when you can't draw. Try this: draw your assets at a super high resolution,
save them as xcf and run this script:

```
; Convert childish drawn images from current folder to pixel art
;
; gimp -i -b '(pixor 20 10)'
(define (pixor new-scale   ; new scale as percent from parent
               pixel-size) ; pixel size from pixelize2
  ; for each file in the current directory
  (let* ( (file's (cadr (file-glob "*.xcf" 1))) (filename "") (image 0) (layer 0) )
    (while (pair? file's)
      ; merge layers
      (set! image (car (gimp-file-load RUN-NONINTERACTIVE (car file's) (car file's))))
      (set! layer (car (gimp-image-merge-visible-layers image CLIP-TO-IMAGE)))
      (set! filename (string-append (substring (car file's) 0 (- (string-length (car file's)) 4)) ".png"))

      ; get original height/width
      (let* ((original-height (car (gimp-image-height image))))
      (let* ((original-width (car (gimp-image-width image))))

        ; apply effects
        (plug-in-pixelize2 RUN-NONINTERACTIVE image layer pixel-size pixel-size)
        (gimp-image-scale-full image (/ (* new-scale original-width) 100) (/ ( * new-scale original-height) 100) INTERPOLATION-CUBIC)

        ; save
        (gimp-file-save RUN-NONINTERACTIVE image layer filename filename)
        (gimp-image-delete image)
        (set! file's (cdr file's))
      ))
    )
  )
  (gimp-quit 0)
)
```

Save it as `pixor.scm` and copy it to gimp scripts folder.

```
cp pixor.scm ~/.gimp-2.8/scripts/
```

Change directory to a folder with your XCF files and run the pixor script.

```
cd /folder/with/src/xcf
gimp -i -b '(pixor 20 10)'
```

The first parameter is the scale of the output image as a percentage from
the input XCF. The second parameter is the pixel size.

The script will cycle though each XCF file in your current directory and export
png images of the flattened visible layers.

Basically makes pixel art from big crappy drawings.
