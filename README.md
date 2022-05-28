# technical-training

step 1:
#required libraries robotstxt,rvest
library(robotstxt)
library(rvest)

step 2:
#SCRAPPING WEBSITE
link<-'https://www.amazon.in/s?bbn=976419031&rh=n%3A976419031%2Cp_89%3AOnePlus&dc&qid=1653641120&rnid=3837712031&ref=lp_976420031_nr_p_89_0'

step 3:
#read url
page<-read_html(link)

step 4:
#segregating data
name<-page%>%html_nodes(".a-size-base-plus")%>%html_text()

price<-page%>%html_nodes(".a-price-whole")%>%html_text()

rating<-page%>%html_nodes(".aok-align-bottom")%>%html_text()

step 5:
#create  a table 
product_reviews=data.frame(name,price,rating)

step 6;
#write data into excel sheet
write.csv(product_reviews,"product_reviews.csv")

step 7:
#view data of products
View(product_reviews)
