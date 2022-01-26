# ggchrisg

The geom you always wished for after drowning in meme cats with ggplot2.
This package is shamelessly cribbed from [ggcats](https://github.com/R-CoderDotCom/ggcats) and is similarly licensed under GPLv3.
The source code of this package is based on `geom_image` from [ggimage](https://cran.r-project.org/web/packages/ggimage/index.html).


<p align="center">
 <img src="https://user-images.githubusercontent.com/67192157/105871532-b0a48700-5ff9-11eb-9371-ecd915ded374.png">
</p>

## Who is Chris G?

Not [John G](https://en.wikipedia.org/wiki/John_Galt).
[Not dead](https://www.dignitymemorial.com/obituaries/washington-dc/christopher-gignoux-6027869) (yet).
Not really a [bushbaby](https://mobile.twitter.com/popgenepi).
Only the coolest G ever Chris-tened.

## Why ggchrisg?

Because Earth without art is just "eh".

## Installation

```r
# install.packages("remotes")
remotes::install_github("klkeys/ggcats@main")
```

## Available images 

There are 6 poses available:

```r
"hagridhoodie" (default), "fistbump", "poser", "madhatter", "professional", "conferencer"
```

## Some examples

```r
grid <- expand.grid(1:3, 2:1)

df <- data.frame(
	x = grid[, 1],
    y = grid[, 2],
    image = c(
		"hagridhoodie",
		"fistbump",
		"poser",
		"madhatter",
		"professional",
		"conferencer"
	)
)
                           
library(ggplot2)
ggplot(df) +
 geom_chrisg(aes(x, y, chrisg = image), size = 5) +
    xlim(c(0.25, 3.5)) + 
    ylim(c(0.25, 2.5))
```

<p align="center">
 <img src="https://user-images.githubusercontent.com/67192157/106767679-6b0c3d80-663b-11eb-96f5-a21f2794bd84.png">
</p>


```r
ggplot(mtcars) +
  geom_chrisg(aes(mpg, wt), chrisg = "hagridhoodie", size = 5)
```

<p align="center">
 <img src="https://user-images.githubusercontent.com/67192157/105848781-c86f1180-5fdf-11eb-8468-813a41235292.png">
</p>


```r
ggplot(mtcars) +
  geom_chrisg(aes(mpg, wt, size = cyl), chrisg = "fistbump")
```

<p align="center">
 <img src="https://user-images.githubusercontent.com/67192157/105849119-416e6900-5fe0-11eb-904e-6dc30be87546.png">
</p>


I took the most part of the following code from [Jonathan Hersh](https://twitter.com/DogmaticPrior).

```r
library(Ecdat)
data(incomeInequality)

library(tidyverse)
library(ggcats)
library(gganimate)


 dat <-
   incomeInequality %>%
   select(Year, P99, median) %>%
   rename(income_median = median,
          income_99percent = P99) %>%
   pivot_longer(cols = starts_with("income"),
                names_to = "income",
                names_prefix = "income_")

dat$chrisg <- rep(NA, 132)

dat$chrisg[which(dat$income == "median")] <- "hagridhoodie"
dat$chrisg[which(dat$income == "99percent")] <- "fistbump" 

ggplot(dat, aes(x = Year, y = value, group = income, color = income)) +
   geom_line(size = 2) +
   ggtitle("ggchrisg, a core package of the turdyverse") +
   geom_chrisg(aes(chrisg = chrisg), size = 5) +
   xlab("Chris G") +
   ylab("Chris G") +
   theme(legend.position = "none",
         plot.title = element_text(size = 20),
         axis.text = element_blank(),
         axis.ticks = element_blank()) +
   transition_reveal(Year)
```

<p align="center">
 <img src="https://user-images.githubusercontent.com/67192157/105854010-9ad99680-5fe6-11eb-9ee0-c42e9e257d48.gif">
</p>
