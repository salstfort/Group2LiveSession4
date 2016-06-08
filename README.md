# Group2LiveSession4

Project: Group 2 Live Session 4 Assignment
Group 2 Live Session 4 members: Antonio Garza, Karen Clark, Marie Wallmark, Salnave Saint-Fort

Description of Project:
Our team was tasked to analyze data for Rolling Sales in Queen from the http://www1.nyc.gov/home/search/index.page?search-terms=Rolling+sales+update website.  The goal of our analysis was to review the data and transform the dataset into a tidy dataset.


First we downloaded the rollingsales_queens.xls file.  The team reviewed the raw data in excel.  First observations.

The rollingsales_queens.xls file was saved as a comma separated file.

Queens <- read.csv("C:\\Users\\kclark\\Personal\\SMU\\Doing Data Science MSDS 6306\\Unit 4\\rollingsales_queens.csv",skip=4,header=TRUE)

Elements of Data File - Original

Borough			                  		Int		

Residential.Units			        		Factor

Neighborhood			            		Factor	

Commerical.Units			        		Factor

Building.Class.Category		    		Factor	

Total.Units				            		Factor

Tax.Class.At.Present	  	    		Factor	

Land.Square.Feet			        		Factor

Block				                  		Int	

Gross.Square.Feet			      			Factor

Lot				                    		Int		

Year.Built				                Int

Ease.Ment			                    Factor	

Tax.Class.At.Time.Of.Sale		      Int

Building.Class.At.Present	        Factor

Building.Class.At.Time.Of.Sale		Factor

Address				                		Factor

Sale.Price												Factor

Apartment.Number		          		Factor

Sale.Date													Factor

Zip.Code			                		Int

Software used:
R version 3.3.0 (2016-05-03)
Platform: x86_64-w64-mingw32/x64 (64-bit)
Running under: Windows 7 x64 (build 7601) Service Pack 1

locale:
[1] LC_COLLATE=English_United States.1252  LC_CTYPE=English_United States.1252    LC_MONETARY=English_United States.1252
[4] LC_NUMERIC=C                           LC_TIME=English_United States.1252    

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
 [1] gdata_2.17.0     reshape2_1.4.1   downloader_0.4   plyr_1.8.3       tidyr_0.4.1      ggplot2_2.1.0   
 [7] countrycode_0.18 jsonlite_0.9.20  WDI_2.4          RJSONIO_1.3-0   

loaded via a namespace (and not attached):
 [1] Rcpp_0.12.5      knitr_1.12.3     magrittr_1.5     munsell_0.4.3    colorspace_1.2-6 R6_2.1.2        
 [7] stringr_1.0.0    dplyr_0.4.3      tools_3.3.0      parallel_3.3.0   grid_3.3.0       gtable_0.2.0    
[13] DBI_0.4          gtools_3.5.0     htmltools_0.3.5  yaml_2.1.13      lazyeval_0.1.10  digest_0.6.9    
[19] assertthat_0.1   rmarkdown_0.9.6  stringi_1.0-1    scales_0.4.0  


--Data Clean up--

-Changed Sales.Price to a numeric variable type instead of a Factor. Also used the pattern “[^[:digit:]]” to identify members of the variable that started with digits and replace them with nothing.

    Queens$SALE.PRICE.N <- as.numeric(gsub("[^[:digit:]]","", Queens$SALE.PRICE))

-Count all instances where Sales.Price value is NA

    count(is.na(Queens$SALE.PRICE.N)) 

- Change all variable names to lower case

    names(Queens) <- tolower(names(Queens))

- Remove leading zeros for Gross.Square.Feet, Land.Square.Feet, and Year.Built

    Queens$gross.sqft <- as.numeric(gsub("[^[:digit:]]","", Queens$gross.square.feet))

    Queens$land.sqft <- as.numeric(gsub("[^[:digit:]]","", Queens$land.square.feet))

    Queens$year.built <- as.numeric(as.character(Queens$year.built))

- Removed all zeros from the Sale.Price field and only keep actual sales

    Queens.sale <- Queens[Queens$sale.price.n!=0,]

Removed Outliers that did not look like actual sales

  First created a variable Queens.homes that included 1, 2, and 3 family homes – total 8146 observations

    Queens.homes <- Queens.sale[which(grepl("FAMILY",Queens.sale$building.class.category)),]

  Then remove outliers from this dataset that do not look like actual sales

    Queens.homes$outliers <- (log(Queens.homes$sale.price.n) <=5) + 0

    Queens.homes <- Queens.homes[which(Queens.homes$outliers==0),]

Copyright:

Data was downloaded from http://www1.nyc.gov/home/search/index.page?search-terms=Rolling+sales+update website. 

Code used to manipulate data was taken from
"Doing Data Science - Straight Talk from the Frontline" by Cathy O'Neill and Rachel Schutt pages 48-50




