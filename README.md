# Example repo for testing holepunch

This repository is an example repo to test out the holepunch` package. It uses a few `tidyverse` packages but also the `dataRetrieval` package for the `yahara_dat` dataset.

To test `holepunch`, follow these steps:

1. Click Use this template to the left of Clone or download.
2. Give this repo a new name and create a new repo in your account
3. Click the Clone or download button, copy the URL.
4. in Rstudio Desktop, click the project drop down on the top right, New Project, Version Control, and paste in the URL of your new GitHub repository

Now in Rstudio

1. Install `holepunch` with `remotes::install_github("karthik/holepunch")`
2. Then run the following code:

```
library(holepunch)
# 🚫🚨No need for install.r or runtime.txt 🚨 🚫
write_compendium_description()
# to write a description, with dependencies listed 
write_dockerfile() 
# To write a dockerfile (more on how to adapt this)
# generate_badge()

# At this time push the code to GitHub 🙌

# And click on the button or use
build_binder()
# 🤞🚀
```

Does clicking the badge launch binder for you? If not, please file an issue.