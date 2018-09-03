# Nuts-project
Darknet yolo v3 tiny model for Nuts detection.
1 class detection
Two models build:
small input for h x w of 416 x 416
big input for h x w of 1024 x 768

There needs to be couple of changes:
1) run it with  -thresh 0.35

2) Code change in src/image.c :

a) void draw_box_width(image a, int x1, int y1, int x2, int y2, int w, float r, float g, float b)
 
// instead of w, use 2 or 3.
    for(i = 0; i < 2; ++i){
        draw_box(a, x1+i, y1+i, x2-i, y2-i, r, g, b);

b) void draw_detections(image im, detection *dets, int num, float thresh, char **names, image **alphabet, int classes)
// Comment draw label to not display the label name on the output stream
//         draw_label(im, top + width, left, label, rgb);
