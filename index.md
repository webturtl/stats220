# Hello!
Welcome to my page. I hope you enjoy my meme :).

## My meme
![](mymeme.png)

I made this meme because:
* I am not a fan of doing uni online
* I found these images and thought that they were a good fit

### CODE
```
library(magick)

## initial dr_zoidberg image
dr_zoidberg <- image_read("https://oyster.ignimgs.com/mediawiki/apis.ign.com/futurama/4/4b/Slinky.jpg") %>%
  image_scale(400)

## cropped dr_zoidberg image
dr_zoidberg_crop <- image_crop(dr_zoidberg, "400x240+0+50")

#fry image
fry <- image_read("https://static3.srcdn.com/wordpress/wp-content/uploads/2019/12/tv-6-futurama-Cropped.jpg?q=50&fit=crop&w=963&h=481&dpr=1.5") %>%
  image_scale(400)

## annotating text box for dr_zoidberg
zoidberg_text <- image_blank(width = 400,
                             height = 240,
                             color = "#fffaef") %>%
  image_annotate(text = "online\nuniversity",
                 color = "#554a42",
                 size = 40,
                 font = "Times New Roman",
                 weight = 700,
                 gravity = "center")

## annotating text box for fry
fry_text <- image_blank(width = 400,
                        height = 200,
                        color = "#fffaef") %>%
  image_annotate(text = "in person\nuniversity",
                 color = "#554a42",
                 size = 40,
                 font = "Times New Roman",
                 weight = 700,
                 gravity = "center")

## combining dr_zoidberg with text box
first_row <- c(dr_zoidberg_crop, zoidberg_text) %>%
  image_append()

## combining fry with text box
second_row <- c(fry, fry_text) %>%
  image_append()

## stacking the two images on top of one another
meme1 <- c(first_row, second_row) %>%
  image_append(stack = TRUE) %>%
  image_scale(700)
  
## creating a border for the entire image
mymeme <- image_border(meme1, "#3d3d3d", "5x5")

image_write(mymeme,"images/mymeme.png")
```

[Back to top](#)
