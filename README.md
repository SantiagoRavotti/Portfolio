# Santiago Ravotti Data Analyst Portfolio

## Analysis of Copenhagen  Rental-rooms with WebScrapping, Python and Tableau

A couple of weeks before I moved to Copenhagen, I wanted to know what I could expect to pay per month for a room in the metropolitan area, as well as the size of the rooms. This, after being added to multiple Whatsapp groups for Expats in Copenhagen, was a common question among those of us who decided to move to Denmark. 

So I decided to do Web Scrapping on the website *boligportal.dk* with Python libraries like BeautifulSoup, request, geopy and Pandas, and get a data frame with zip codes, areas, sizes and prices. Here's some of the code:

```
add = 18
while add <= 1730:
    url = "https://www.boligportal.dk/en/rental-apartments/k%C3%B8benhavn/?offset="+str(add)
#this will allow us to go to the next page and the following one once the loop is completed
    response = requests.get(url)
    data = response.content
    sopa = soup(data, "lxml")
    appartments = sopa.find_all('div', {'class': 'css-1jf5j4m'})
    for raw in appartments:
        for price in sopa.find_all('span', {'class': 'css-1wltohh'}):
            price_list.append(price.text)
        for location in sopa.find_all('div', {'class': 'css-22506a'}):
            location_list.append(location.text)
        for size in sopa.find_all('div', {'class': 'css-5oox4j'}):
            size_list.append(size.text)
        break
    add=add+18
```

Once I finished cleaning, replacing, sorting and deleting data in Excel, I proceeded to visualise this data in Tableau. Here is some visual result of the project.

![First Image](Analysis%20of%20Room%20Prices%20Copenhagen.JPG)

We can easily observe, among other aspects, how the average price of a room in Copenhagen is 5,829 kr per month and how prices decrease as we move away from the city centre. 

 - If you are interested in the Python code and steps to get the data and place it inside a Pandas dataframe, check the GitHub repository at the following link, where you will find a Jupyther Notebook with all the steps:

### [GitHub Repository](https://github.com/SantiagoRavotti/Copenhagen-Apartments-Analysis)

 - If you want to see the visualisations interactively in my Tableau Public, this is the link to my profile: 

### [Tableau Profile](https://public.tableau.com/app/profile/luis.santiago.ravotti)
