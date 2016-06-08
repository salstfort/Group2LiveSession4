# Group2LiveSession4

Project: Group 2 Live Session 4 Assignment
Group 2 Live Session 4 members: Antonio Garza, Karen Clark, Marie Wallmark, Salnave Saint-Fort

Description of Project:
Our team was tasked to analyze data for Rolling Sales in Queen from the http://www1.nyc.gov/home/search/index.page?search-terms=Rolling+sales+update website.  The goal of our analysis was to review the data and transform the dataset into a tidy dataset.


First we downloaded the rollingsales_queens.xls file.  The team reviewed the raw data in excel.  First observations.

The rollingsales_queens.xls file was saved as a comma separated file.

Queens <- read.csv("YOUR WORKING DIRECTORY\\rollingsales_queens.csv",skip=4,header=TRUE)

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


Data Cleanup was completed all documentation and code executed is in the Data folder in then AGarzaKLClarkMFWallmarkSSaintFort_RCleanupCode.txt. file

Completed Analysis is detailed in the Analysis folder in Week_4_Group_Project_Analysis.md file.  

Conclusion:
The focus of the analysis was comparing the Gross Square Foot to the Sales Price of 1, 2, and 3 Family homes. The original data was right skewed so a log transformation of 10 was applied to the dataset to correct this.


Copyright:

Data was downloaded from http://www1.nyc.gov/home/search/index.page?search-terms=Rolling+sales+update website. 

Code used to manipulate data was taken from
"Doing Data Science - Straight Talk from the Frontline" by Cathy O'Neill and Rachel Schutt pages 48-50




