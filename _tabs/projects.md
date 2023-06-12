---
# the default layout is 'page'
icon: fas fa-briefcase
order: 2
images:
  - path: /assets/chicken_pixel.jpeg
    column: 1
    text: Image 1
  - path: /assets/chicken_pixel.jpeg
    column: 2
    text: Image 2
  - path: /assets/chicken_pixel.jpeg
    column: 3
    text: Image 3
---
<div class="container">
<div class="row">
<img src="{{page.images[0].path}}" class="col-sm" width="500" height="600">
<img src="{{page.images[0].path}}" class="col-sm" width="500" height="600">
<img src="{{page.images[0].path}}" class="col-sm" width="500" height="600">
</div>
</div>
