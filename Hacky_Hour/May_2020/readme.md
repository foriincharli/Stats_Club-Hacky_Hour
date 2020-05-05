# R Markdown Tutorial - Hacky Hour"
## May 6th, 2020

## Aims

  1. Understand what R Markdown is
  2. Construct an R Markdown file
  3. Export your R Markdown file

## R Markdown

R Markdown allows researchers to create documents that record their analysis by presenting code alongside its output. The notebook-like outputs make it easier to understand what was done when revisiting old code, improves reproducibility and is more collaborator and supervisor friendly than pure R scripts.

R Markdown can render to many different file formats, like HTML, Word documents, and pdf. When knitting to .docx, the headings aesthetics are inherited from Word.

For today's tutorial we are going to learn how to create an R Markdown document to record our analyses.

## Creating an R Markdown file

To create a new RMarkdown file (`.Rmd`), select `File -> New File -> R Markdown...` in RStudio, then choose the file type you want to create. For now we will focus on a `.html` document, which can be easily converted to other file types later.

By default the newly-created `.Rmd` file comes with some basic instructions and a header populated with information we provided, like the name of the document and the author.

## Formatting options
Please refer to the R Markdown cheat sheet for formatting options like bold/italic font, headers and lists.

[![Image name](rmd_cheatsheet.png)](https://rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf)

## Code chunks
Unlike an R script, text is treated like documentation in R Markdown unless it is within code chunks. To write code that can be executed, we need to use code chunks. Chunks are enclosed by two sets of three grave accents ``` (found on the same button as the tilde) and contain information regarding the language, name of the chunk and any options regarding how the code is output in the R Markdown document inside curly brackets.

To insert a new chunk:

  * Click the *Insert Chunk* button on the toolbar
  * Press *Cmd + Option + i* (Mac)
  * Press *Ctrl + Alt + i* (Windows)
  
To execute a chunk:

  * Click *Run* within the chunk
  * Place the cursor inside and press *Cmd + Shift + Enter* or *Cmd + Enter* (Mac)
  * Place the cursor inside and press *Ctrl + Shift + Enter* or *Ctrl + Enter* (Windows)

The contents of the curly brackets provide instructions to the compiler about how the code should be executed. The curly brackets for the chunk below contain the following: `{r calculator_chunk, include = TRUE}`. 

These instructions provide the following pieces of information to the compiler:

  1. The code is R code `r`
  2. The name of the chunk is `calculator_chunk`
  3. The code should be included along with the output `include = TRUE`

**Note: chunk names must be unique, or it will give an error**

```r
# convert Fahrenheit to Celsius
paste("Temperature in Celsius:", round(((360 - 32) * 5/9), 2))
```


If you are creating an R Markdown file that you want to run that refers to an object, you must create that object first. 
```r
plot(houseplants)
```

Attempting to use an object called 'houseplants' that doesn't already exist in the environment throws an error. 

Similarly, if you're loading a dataframe from a `.csv` or a `.txt` document, you must include the code in the `.Rmd`.

```r
houseplants <- read.csv("/Desktop/folder/houseplants.csv")
```


```r
houseplants <- c("Fiddle leaf fig", "Swiss cheese plant", "Zanzibar Gem", "Chinese Money Plant", "Cactus") 
height_cm <- c(167, 92, 55, 23, 11)
colour <- c("Malachite", "Viridian", "Smaragdine", "Emerald", "Celadon")
plants <- data.frame(houseplants, height_cm, colour)
```

```{r print_str_plants}
str(plants)
print(plants)
```


If you're using any packages in your analysis, these will also needed to be loaded as you would in a normal `R` script. For example:
```{r, eval = FALSE}
library(dplyr)
```


## Chunk options

| Instruction        | Default           | Function  |
|:-------------:|:-------------:| ------------- |
| eval      | eval = TRUE | Run code and include the results in the output |
| include      | include = TRUE      | Include the code and the results in the output |
| echo | echo = TRUE | Display the code alongside the results |
| warning | warning = TRUE | Display warning messages |
| error | error = FALSE | Display error messages |
| message | message = TRUE | Display messages |
| tidy | tidy = FALSE | Reformat the code to make it look tidy |
| results | results = "markup" | Choose how results are treated - "hide", "asis", "hold" |
| cache | cache = FALSE | Cache results for future renders |
| comment | comment = "##" | Preface comments with a character |
| fig.width | fig.width = 7 | Set width of plots/figures (inches) |
| fig.height | fig.height = 7 | Set height of plots/figures (inches) |
| fig.align | fig.align = "center" | Set alignment of plot/figure in document - "left", "right", "center" |
| fig.cap | fig.cap = "figure caption" | Write something about your plot/figure |






## Resources
For more details on using R Markdown see <http://rmarkdown.rstudio.com>

Getting started with R Markdown <https://ourcodingclub.github.io/tutorials/rmarkdown/>

Pimp my rmd <https://holtzy.github.io/Pimp-my-rmd/>

Prettier tables with lemon <https://cran.csiro.au/web/packages/lemon/vignettes/lemon_print.html>
