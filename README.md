# Example repo for testing `holepunch`

This repository is an example repo to test out the [`holepunch`](https://github.com/karthik/holepunch) package. It uses a few `tidyverse` packages but also the `dataRetrieval` package for the `yahara_dat` dataset.

<!-- badges: start -->
  [![Launch Rstudio Binder](http://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/karthik/binder-test/master?urlpath=rstudio)
  <!-- badges: end -->
  
  

To test `holepunch`, follow these steps:

1. Click Use this template to the left of Clone or download.
![template](https://i.imgur.com/TcLpIvM.png)
2. Give this repo a new name and create a new repo in your account
3. Click the Clone or download button, copy the URL.

![](https://i.imgur.com/0KEJZ9s.png)

4. in RStudio Desktop, click the Project drop down on the top right, Choose **New Project** > **Version Control** > **Git**, and paste in the URL of your new GitHub repository

![](https://i.imgur.com/oJOV1ng.png)  

![](https://i.imgur.com/n3RZrMc.png)  

![](https://i.imgur.com/CJcAKR1.png)  

![](https://i.imgur.com/ieEmPRU.png)  


# Now in RStudio

1. Install `holepunch` with `remotes::install_github("karthik/holepunch")`
2. Then run the following code:

```r
library(holepunch)
write_compendium_description(package = "Your compendium name", 
                             description = "Your compendium description")
# to write a description, with dependencies listed 
# It's good practice to now go fill in the placeholder text.

write_dockerfile(maintainer = "your_name") 
# To write a dockerfile. It will automatically pick the date of the last modified file, match it to 
# that version of R and add it here. You can override this by passing r_date to some arbitrary date
# (but one for which a R version exists).

generate_badge()
# This generates a badge for your readme.

# At this time 🙌 push the code to GitHub 🙌
# If you're new to Git/GitHub, you can click the Git tab on Rstudio, then click commit to see
# all changed files/folders, including the hidden .binder folder. Give this a commmit message and push

# And click on the badge or use the function below to get the binder built ahead of time.
build_binder()
# 🤞🚀

Now, run through analysis.R till you get to a plot
```

Does clicking the badge launch binder for you? If not, please [file an issue](https://github.com/karthik/binder-test/issues/new).
