

</center>
<style>h1 {text-align: center;}</style>
<h1><b>Workshop Schedule</b></h1>
</center>


***


## **Day 1**
<div class="center-table" markdown>

| **Lesson**                                        | **Overview** | **Instructor** | **Time** |
|:---------------------------------------------------|:-------------|:-------------|:-------------|
|[Workshop Introduction](./day_1/D1.1_intro_to_R_workshop_all.pdf){ .md-button .md-button--primary} | Welcome and housekeeping | Will | 10:00-10:30 |
|[Intro to R and RStudio](./day_1/D1.2_introR-R-and-RStudio.md){ .md-button .md-button--primary} | Introduction to R and RStudio| Elizabeth | 10:30-11:45 |
|[Self learning materials](#){ .md-button .md-button--primary} |Overview of self-learning materials | Will | 11:45-12:00 |

</div>


### **Before the next class** 
A. Please study the contents and work through all the code within the following lessons.

B. **Complete the exercises:**

- Each lesson above contains exercises; please go through each of them.

- Copy over your solutions into the Google Form using the submit link below the day before the next class

Questions?

If you get stuck due to an error while running code in the lesson, [email us](mailto:hbctraining@hsph.harvard.edu)

<div class="grid cards" markdown>

- [__1. R Syntax and Data Structure__](./day_1_exercise/D1.1e_r_syntax_and_data_structures.md)
    
    ??? info "About data types and data structure"
        In order to utilize R effectively, you will need to understand what types of data you can use in R and also how you can store data in "objects" or "variables".

        This lesson will cover:

        - Assigning a value to a object

        - What types of information can you store in R

        - What are the different objects that you can use to store data in R
</div>

<div class="grid cards" markdown>

- [__2. Functions and Arguments__](./day_1_exercise/D1.2e_functions_and_arguments.md)

    ??? info "Functions and Arguments in R"
        Functions are the basic "commands" used in R to get something done. To use functions (denoted by function_name followed by "()"), one has to enter some information within the parenthesis and optionally some arguments to change the default behavior of a function.

        You can also create your own functions! When you want to perform a task or a series of tasks more than once, creating a custom function is the best way to go.

        In this lesson you will explore:

        - Using built-in functions

        - Creating your own custom functions
</div>

<div class="grid cards" markdown>

- [__3. Reading in and inspecting data__](./day_1_exercise/D1.3e_reading_in_and_data_inspection.md)

    ??? info "Read and inspect data structures in R"
        When using R, it is almost a certainty that you will have to bring data into the R environment.

        In this lesson you will learn:

        - Reading different types (formats) of data

        - Inspecting the contents and structure of the dataset once you have read it in
</div>

<div class="grid cards" markdown>

- [__Submit here__::material-email-fast:](https://docs.google.com/forms/d/e/1FAIpQLSfL04I7TVfs5At3n7OCLBieUsJ8nxZgjbO6mQQwCzKoBG1iLA/viewform)
    
    !!! success "Submit a day before the next class."

</div>


## **Day 2**
<div class="center-table" markdown>

| **Lesson**                                        | **Overview** | **Instructor** | **Time** |
|:---------------------------------------------------|:-------------|:-------------|:-------------|
|[Review self-learning](#before-the-next-class){ .md-button .md-button--primary } | Questions about self-learning| All | 10:00-10:50 |
|[In-class exercises ](./day_2/D2.1_in_class_exercises.md){ .md-button .md-button--primary } | Use and customize function and arguments| Elizabeth | 10:50-11:15 |
|[Data Wrangling](./day_2/D2.2_data_wrangling.md){ .md-button .md-button--primary} |Subsetting Vectors and Factors | Will | 11:15-12:00 |

</div>


### **Before the next class** 

A. Please study the contents and work through all the code within the following lessons.

B. **Complete the exercises:**

- Each lesson above contains exercises; please go through each of them.

- Copy over your solutions into the Google Form using the submit link below the day before the next class

Questions?

If you get stuck due to an error while running code in the lesson, [email us](mailto:hbctraining@hsph.harvard.edu)


<div class="grid cards" markdown>

- [__1. Packages and libraries__](./day_2_exercise/D2.1e_packages_and_libraries.md)
    
    ??? info "Installing and loading packages in R"
        Base R is incredibly powerful, but it cannot do everything. R has been built to encourage community involvement in expanding functionality. Thousands of supplemental add-ons, also called "packages" have been contributed by the community. Each package comprises of several functions that enable users to perform their desired analysis.

        This lesson will cover:

        - Descriptions of package repositories

        - Installing a package
        
        - Loading a package
        
        - Accessing the documention for your installed packages and getting help
</div>

<div class="grid cards" markdown>

- [__2. Data wrangling: data frames, matrics and lists__](./day_2_exercise/D2.2e_introR-data-wrangling.md)

    ??? info "Subset, merge, and create new datasets"
        In class we covered data wrangling (extracting/subsetting) information from single-dimensional objects (vectors, factors). The next step is to learn how to wrangle data in two-dimensional objects.

        This lesson will cover:
        
        - Examining and extracting values from two-dimensional data structures using indices, row names, or column names
        
        - Retreiving information from lists
</div>

<div class="grid cards" markdown>

- [__3. The %in% operator__](./day_2_exercise/D2.3e_identifying-matching-elements.md)

    ??? info "`%in%` operator, `any` and `all` functions"
        Very often you will have to compare two vectors to figure out if, and which, values are common between them. The %in% operator can be used for this purpose.

        This lesson will cover:
        
        - Implementing the %in% operator to evaluate two vectors
        
        - Distinguishing %in% from == and other logical operators
        
        - Using any() and all() functions

</div>

<div class="grid cards" markdown>

- [__4. Reordering and matching__](./day_2_exercise/D2.4e_reordering-to-match-datasets.md)

    ??? info "Ordering of vectors and data frames"
        Sometimes you will want to rearrange values within a vector (row names or column names). The match() function can be very powerful for this task.

        This lesson will cover:

        - Maunually rearranging values within a vector

        - Implementing the match() function to automatically rearrange the values within a vector
</div>

<div class="grid cards" markdown>

- [__5. Data frame for plotting__](./day_2_exercise/D2.5e_setting_up_to_plot.md)

    ??? info "Learn about `map()` function for iterative tasks"
        We will be starting with visualization in the next class. To set up for this, you need to create a new metadata data frame with information from the counts data frame. You will need to use a function over every column within the counts data frame iteratively. You could do that manually, but it is error-prone; the map() family of functions makes this more efficient.

        This lesson will cover:
        
        - Utilizing map_dbl() to take the average of every column in a data frame
        
        - Briefly discuss other functions within the map() family of functions
        
        - Create a new data frame for plotting
</div>

<div class="grid cards" markdown>

- [__Submit here__:material-email-fast:](https://docs.google.com/forms/d/e/1FAIpQLSegEjBKDkK4TB7uhNfcBl6633hasPrGsYDnFuH683blpZNtfg/viewform)
    
    !!! success "Submit a day before the next class."

</div>

**Prepare for in-class exercise:**

- Download the data and place the file into the `data` directory.

|Data | Download link |
|:------|:--------|
|Animal data |[Right click & Save link as...](https://raw.githubusercontent.com/hbctraining/Intro-to-R-flipped/master/data/animals.csv){ .md-button}|

- Read the .csv file into your environment and assign it to a variable called animals. 
    *Be sure to check that your row names are the different animals.*

 - Save the R project when you close Rstudio.



* * *

## **Day 3**
<div class="center-table" markdown>

| **Lesson**                                        | **Overview** | **Instructor** | **Time** |
|:---------------------------------------------------|:-------------|:-------------|:-------------|
|[Review self-learning](#before-the-next-class-1){ .md-button .md-button--primary } | Questions about self-learning| All | 10:00-10:35 |
|[In-class exercises ](./day_3/D3.1_in_class_exercises.md){ .md-button .md-button--primary } | Customizing functions and arguments| Will | 10:50-11:15 |
|[Plotting with ggplot2](./day_3/D3.2_plotting_with_ggplot2.md){ .md-button .md-button--primary} | ggplot2 for data visualization | Elizabeth | 11:15-12:00 |

</div>


### **Before the next class** 

1. Please study the contents and work through all the code within the following lessons.

2. **Complete the exercises:**

- Each lesson above contains exercises; please go through each of them.

- Copy over your solutions into the Google Form using the submit link below the day before the next class

Questions?

If you get stuck due to an error while running code in the lesson, [email us](mailto:hbctraining@hsph.harvard.edu)

<div class="grid cards" markdown>

- [__1. Custom functions for plots__](./day_3_exercise/D3.1e_Custom_Functions_ggplot2.md)
    
    ??? info "Consistent formats for plotting"
        When creating your plots in ggplot2 you may want to have consistent formatting (using theme() functions) across your plots, e.g. if you are generating plots for a manuscript.

        This lesson will cover:
        
        - Developing a custom function for creating consistently formatted plots
</div>

<div class="grid cards" markdown>

- [__2. Boxplot with ggplot2__](./day_3_exercise/D3.2e_boxplot_exercise.md)

    ??? info "Customizing barplots with ggplot2"
        Previously, you created a scatterplot using ggplot2. However, ggplot2 can be used to create a very wide variety of plots. One of the other frequently used plots you can create with ggplot2 is a barplot.

        This lesson will cover:
        
        - Creating and customizing a barplot using ggplot2  
</div>

<div class="grid cards" markdown>

- [__3. Exporting files and plots__](./day_3_exercise/D3.3e_exporting_data_and_plots.md)

    ??? info "Writing files and plots in different formats"
        Now that you have completed some analysis in R, you will need to eventually export that work out of R/RStudio. R provides lots of flexibility in what and how you export your data and plots.

        This lesson will cover:
        
        - Exporting your figures from R using a variety of file formats
        
        - Writing your data from R to a file
</div>

<div class="grid cards" markdown>

- [__4. Finding help__](./day_3_exercise/D3.4e_finding_help.md)

    ??? info "How to best look for help"
        Hopefully, this course has given you the basic tools you need to be successful when using R. However, it would be impossible to cover every aspect of R and you will need to be able to troubleshoot future issues as they arise.

        This lesson will cover:
        
        - Suggestions for how to best ask for help
        
        - Where to look for help
</div>

<div class="grid cards" markdown>

- [__5. Tidyverse__](./day_3_exercise/D3.5e_tidyverse.md)

    ??? info "Data wrangling within Tidyverse"
        The Tidyverse suite of integrated packages are designed to work together to make common data science operations more user friendly. Tidyverse is becoming increasingly prevalent and it is necessary that R users are conversant in the basics of Tidyverse. We have already used two Tidyverse packages in this workshop (ggplot2 and purrr) and in this lesson we will learn some key features from a few additional packages that make up Tidyverse.

        This lesson will cover:
    
        - Usage of pipes for connecting together multiple commands
    
        - Tibbles for two-dimensional data storage
    
        - Data wrangling within Tidyverse
</div>

<div class="grid cards" markdown>

- [__Submit here__:material-email-fast:](https://docs.google.com/forms/d/e/1FAIpQLSdelYtXxCGQZOWd2T28REjU5NC_NS4n-HZte8OEgFXS6Q5wcA/viewform)
    
    !!! success "Submit a day before the next class."

</div>


* * *

## **Day 4**
<div class="center-table" markdown>

| **Lesson**                                        | **Overview** | **Instructor** | **Time** |
|:---------------------------------------------------|:-------------|:-------------|:-------------|
|[Review self-learning](#before-the-next-class-2){ .md-button .md-button--primary } | Questions about self-learning| All | 10:00-10:35 |
|[In-class exercises ](./day_4/D4.1_in_class_exercises.md){ .md-button .md-button--primary } | In class exercises| Elizabeth | 10:50-11:15 |
|[Discussion](./#){ .md-button .md-button--primary} | Q&A | Will | 11:15 - 11:45 |
|[Wrap Up](./day_4/D4.2_R_workshop_wrapup_all.pdf){ .md-button .md-button--primary} | Wrap up and checking out| Will | 11:45 - 12:00 |

</div>


### **Additional exercises and answer keys**

<div class="grid cards" markdown>

- [__Final Exercises__](./day_4_exercise_n_answer_keys/D4.1e_intro_to_R_hw.md)

</div>


<div class="grid cards" markdown>

??? info "Answer Keys"
    - [Answer Keys Day 1](./day_4_exercise_n_answer_keys/Day1_Homework_Answer-Key.md)
    - [Answer Keys Day 2](./day_4_exercise_n_answer_keys/Day2_Homework_Answer-Key.md)
    - [Answer Keys Day 3](./day_4_exercise_n_answer_keys/Day3_Homework_Answer-Key.md)
    - [Answer Keys Final exercise](./day_4_exercise_n_answer_keys/Day4_Intro_to_R_Answer-Key.md)

</div>


### **Additional resources**


<div class="grid cards" markdown>

- __Building on the basic R knowledge__
    - [DGE workshop](https://hbctraining.github.io/DGE_workshop_salmon/)
    - [Single-cell RNA-seq workshop](https://hbctraining.github.io/scRNA-seq/)
    - [RMarkdown](https://hbctraining.github.io/Training-modules/Rmarkdown/)
    - [Functional analysis](https://hbctraining.github.io/Training-modules/DGE-functional-analysis/)
    - [More ggplot2](https://hbctraining.github.io/publication_perfect/)
    - [ggplot2 cookbook](http://www.cookbook-r.com/Graphs/)
    - [Running R and Rstudio on O2](https://harvardmed.atlassian.net/wiki/spaces/O2/pages/1594262976/Intro+to+R+Bioconductor)

- __Resources__
    - [Online learning resources](https://hbctraining.github.io/bioinformatics_online/lists/online_trainings.html)
    - [All hbctraining materials](https://hbctraining.github.io/main)
  
    __Cheatsheets__

    - [base R cheatsheet](https://github.com/hbctraining/Intro-to-R-flipped/blob/master/cheatsheets/base-r.pdf)
    - [RStudio cheatsheet](https://github.com/hbctraining/Intro-to-R-flipped/blob/master/cheatsheets/rstudio-ide.pdf)
    - [ggplot2 cheatsheet](https://github.com/hbctraining/Intro-to-R-flipped/blob/master/cheatsheets/data-visualization-2.1.pdf)

</div>

* * * 


!!!quote "Attribution & Citation"    

    * *These materials have been developed by members of the teaching team at the [Harvard Chan Bioinformatics Core (HBC)](http://bioinformatics.sph.harvard.edu/). These are open access materials distributed under the terms of the [Creative Commons Attribution license](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0), which permits unrestricted use, distribution, and reproduction in any medium, provided the original author and source are credited.*

    * *Some materials used in these lessons were derived from work that is Copyright © [Data Carpentry](http://datacarpentry.org/). All Data Carpentry instructional material is made available under the [Creative Commons Attribution license (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)*


     * *To cite material from this course in your publications, please use:*

        **Meeta Mistry, Mary Piper, Jihe Liu, & Radhika Khetani. (2021, May 5). hbctraining/Intro-to-R-flipped: R workshop first release. Zenodo. https://doi.org/10.5281/zenodo.4739342**

    * A lot of time and effort went into the preparation of these materials. Citations help us understand the needs of the community, gain recognition for our work, and attract further funding to support our teaching activities. Thank you for citing this material if it helped you in your data analysis.
