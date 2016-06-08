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


Data Clean up
1.	Changed Sales.Price to a numeric variable type instead of a Factor. Also used the pattern “[^[:digit:]]” to identify members of the variable that started with digits and replace them with nothing.
Queens$SALE.PRICE.N <- as.numeric(gsub("[^[:digit:]]","", Queens$SALE.PRICE))
 
2.	Count all instances where Sales.Price value is NA
count(is.na(Queens$SALE.PRICE.N)) 

3.	Change all variable names to lower case 
names(Queens) <- tolower(names(Queens))

4.	Remove leading zeros for Gross.Square.Feet, Land.Square.Feet, and Year.Built
Queens$gross.sqft <- as.numeric(gsub("[^[:digit:]]","", Queens$gross.square.feet))
Queens$land.sqft <- as.numeric(gsub("[^[:digit:]]","", Queens$land.square.feet))
Queens$year.built <- as.numeric(as.character(Queens$year.built))

5.	Removed all zeros from the Sale.Price field and only keep actual sales
Queens.sale <- Queens[Queens$sale.price.n!=0,]

6.	Removed Outliers that did not look like actual sales

•	First created a variable Queens.homes that included 1, 2, and 3 family homes – total 8146 observations
Queens.homes <- Queens.sale[which(grepl("FAMILY",Queens.sale$building.class.category)),]

•	Then remove outliers from this dataset that do not look like actual sales
Queens.homes$outliers <- (log(Queens.homes$sale.price.n) <=5) + 0
Queens.homes <- Queens.homes[which(Queens.homes$outliers==0),]

Final File Layout:



Analysis:

Conclusion:





