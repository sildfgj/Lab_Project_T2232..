DSC 200 Lab Project -Term 2232
================
2024-05-20

**Student Name:<insert your name here>**wajdan..

**Student ID:<insert ID here>**2221003984

**Deadline:** 23:59 on Sunday, 19 May 2024

**Total Points:** 20

## Loading Packages

``` r
library(tidyverse)
library(openintro)
library(ggrepel)
```

## Tasks

\`1. (2 points) \`\`\`{r}num_pets \<- nrow(seattlepets) num_pets

    Write your narrative We use the nrow() function to count the number of rows in the seattlepets dataset, which gives us the number of pets included in the dataset. 




    `2. (2 points)

    ```{r}num_variables <- ncol(seattlepets)
    num_variables

Write your narrative below We use the ncol() function to count the
number of columns in the seattlepets dataset, which gives us the number
of variables for each pet.

\`3. (2 points) \`\`\`{r}species_count \<- seattlepets %\>%
count(species) %\>% arrange(desc(n)) species_count

    Write your narrative here We use the count() function to count the number of pets for each species in the seattlepets dataset. Then we arrange the results in descending order using the arrange(desc(n)) function.


    `4. (2 points)
    ```{r}common_pet_names <- seattlepets %>%
      count(animal_name) %>%
      arrange(desc(n)) %>%
      top_n(10)
    common_pet_names

Write your narrative here We use the count() function to count the
frequency of each pet name in the seattlepets dataset. Then we arrange
the results in descending order using the arrange(desc(n)) function and
select the top ten most common names using the top_n(10) function.

\`5. (2 points) \`\`\`{r}pig_records \<- seattlepets %\>% filter(species
== “Pig”) %\>% arrange(animal_name) pig_records

    Write your narrative her eWe use the filter() function to filter the records where the species is "Pig". Then we arrange the results by pet names using the arrange(animal_name) function




    `6. (2 points)
    ```{r}goat_records <- seattlepets %>%
      filter(species == "Goat") %>%
      select(animal_name, primary_breed) %>%
      arrange(animal_name)
    goat_records

Write your narrative here We use the filter() function to select the
records where the species is “Goat”. Then we use the select() function
to choose the columns animal_name and primary_breed. Finally, we sort
the results by pet names using the arrange(animal_name) function

\`7. (2 points) \`\`\`{r}merged_columns \<- seattlepets %\>% mutate(pet
= paste(animal_name, species, sep = “;”)) %\>% select(license_number,
pet) %\>% arrange(pet) merged_columns

    Write your narrative here We use the mutate() function to add a new column pet which concatenates the values from animal_name and species using the paste() function with a separator "; ". Then we use the select() function to choose the columns license_number and pet. Finally, we sort the results by the pet column using the arrange(pet) function.



    `8. (2 points)
    ```{r}species_plot <- seattlepets %>%
      ggplot(aes(x = species)) +
      geom_bar() +
      labs(title = "Counts of Pet Species in Seattle", x = "Species", y = "Count") +
      theme_minimal()

    species_plot

Write your narrative here We use ggplot2 to create a bar plot displaying
the counts of pet species. We specify species as the x-axis using aes(x
= species), then use geom_bar() to create the bars. We add a title and
labels for the axes using labs(), and apply a minimal theme with
theme_minimal() to improve the appearance of the plot.

\`9. (2 points)

``` r
top_10_names <- seattlepets %>% 
filter(animal_name %in% c( "Lucy"  , "Charlie" , "Luna" , "Bella" , "Max"    , 
                           "Daisy" , "Molly"   , "Jack" , "Lily"  , "Stella" ))
top_10_names
```

    ## # A tibble: 2,974 × 7
    ##    license_issue_date license_number animal_name species primary_breed          
    ##    <date>             <chr>          <chr>       <chr>   <chr>                  
    ##  1 2018-11-25         S120480        Charlie     Dog     Retriever, Labrador    
    ##  2 2018-11-03         829563         Max         Dog     Retriever, Labrador    
    ##  3 2018-10-29         732106         Lily        Cat     Domestic Shorthair     
    ##  4 2018-11-25         895808         Max         Cat     Domestic Shorthair     
    ##  5 2018-11-26         834841         Daisy       Dog     Terrier, American Pit …
    ##  6 2018-12-13         8003804        Charlie     Dog     Border Collie          
    ##  7 2018-11-06         S125292        Jack        Cat     Domestic Shorthair     
    ##  8 2018-11-01         835179         Stella      Dog     Retriever, Labrador    
    ##  9 2018-12-14         950094         Molly       Dog     Retriever, Labrador    
    ## 10 2018-11-24         S137301        Lucy        Dog     Hound                  
    ## # ℹ 2,964 more rows
    ## # ℹ 2 more variables: secondary_breed <chr>, zip_code <chr>

\`a. What does the above code chunk do? This code defines a vector
top_10_names that contains the 10 most common pet names identified in
Task 4. This list will be used to filter and analyze the dataset for
these specific pet names.

\`b. Plot the counts of the pet names (animal_name) in top_10_names
\`\`\`{r}top_10_plot \<- top_10_data %\>% ggplot(aes(x = animal_name,
fill = species)) + geom_bar(position = “dodge”) + labs(title = “Counts
of Top 10 Pet Names Segmented by Species”, x = “Pet Name”, y = “Count”,
fill = “Species”) + theme_minimal()

top_10_plot

\`\`\`Ex: 1. We filter the seattlepets dataset to include only the
records where animal_name is in top_10_names using filter(animal_name
%in% top_10_names). 2. We then use ggplot2 to create a bar plot where
the x-axis represents animal_name and the fill color represents the
species. The geom_bar(position = “dodge”) creates a bar plot with bars
for different species side by side. 3. Finally, we add labels and a
minimal theme for better readability.:

\`10. (2 points)

\`The below code plots the proportion of dogs with a given name versus
the proportion of cats with the same name. The 20 most common cat and
dog names are displayed. The diagonal line on the plot is the x = y
line; if a name appeared on this line, the name’s popularity would be
exactly the same for dogs and cats.

    ## Warning: Using `size` aesthetic for lines was deprecated in ggplot2 3.4.0.
    ## ℹ Please use `linewidth` instead.
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

    ## Warning in geom_image(mapping, data, inherit.aes = inherit.aes, na.rm = na.rm, : All aesthetics have length 1, but the data has 20 rows.
    ## ℹ Please consider using `annotate()` or provide this layer with data containing
    ##   a single row.
    ## All aesthetics have length 1, but the data has 20 rows.
    ## ℹ Please consider using `annotate()` or provide this layer with data containing
    ##   a single row.

![](Lab_project_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

\`What names are more common for cats than dogs? The ones above the line
or the ones below the line?

\`Answer here In the plot, names that are more common for cats than dogs
will be above the diagonal line $x = y$. This is because the proportion
of cats with these names is higher than the proportion of dogs with the
same names.

\`Is the relationship between the two variables (proportion of cats with
a given name and proportion of dogs with a given name) positive or
negative? What does this mean in context of the data?

\`Answer here The relationship between the proportion of cats with a
given name and the proportion of dogs with the same name is positive.
This means that names that are popular for cats tend to also be popular
for dogs. In the context of the data, it indicates a general trend where
pet names are chosen similarly for both species, although specific names
might be slightly more popular for one species over the other.
