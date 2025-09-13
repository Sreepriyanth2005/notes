
#### Data Scraping

Data scraping, in its most general form, refers to a technique in which a computer program extracts data from output generated from another program. Data scraping is commonly manifested in web scraping, the process of using an application to extract valuable information from a website.

#### Types

1. Content - To Scrape like description, Content Based.
2. Price - To extract cost of products (Amazon, Flipkart)
3. Contact - To extract email address and numbers like contacts

#### BS4's Beautiful Soup

Beautiful Soup is a Python library for pulling data out of HTML and XML files. It works with parser to provide idiomatic ways of navigating, searching, and modifying the parse tree.

#### Why parser is used?

The **parser** in BeautifulSoup is essential because it tells BeautifulSoup **how to interpret and structure the HTML or XML content**. HTML from websites is often **messy, incomplete, or poorly formatted**, so the parser's job is to **convert that raw HTML into a readable, navigable tree structure**.

Without a parser, BeautifulSoup cannot know how to read the HTML correctly.

| Parser               | Typical usage                                                      | Advantages                                                                                                     | Disadvantages                                       |
| -------------------- | ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| Python's html.parser | `BeautifulSoup(markup, "html.parser")`                             | - Batteries included<br>    <br>- Decent speed                                                                 | - Not as fast as lxml, less lenient than html5lib.  |
| lxml's HTML parser   | `BeautifulSoup(markup, "lxml")`                                    | - Very fast                                                                                                    | - External C dependency                             |
| lxml's XML parser    | `BeautifulSoup(markup, "lxml-xml")` `BeautifulSoup(markup, "xml")` | - Very fast<br>    <br>- The only currently supported XML parser                                               | - External C dependency                             |
| html5lib             | `BeautifulSoup(markup, "html5lib")`                                | - Extremely lenient<br>    <br>- Parses pages the same way a web browser does<br>    <br>- Creates valid HTML5 | - Very slow<br>    <br>- External Python dependency |

#### Try :

- https://books.toscrape.com
- https://quotes.toscrape.com

### Sample Scraping for Books(without next)

```python
from bs4 import BeautifulSoup
import requests

url="https://books.toscrape.com
header={"User-Agent":"Mozilla/5.0"}
html=requests.get(url,headers=header)
soup=BeautifulSoup(html.text,"html.parser")
ol=soup.find("ol")
products=[]
for li in ol.find_all("li"):
    h3=li.find("h3")
    a=h3.find("a")
    title=a.get("title")
    prod=li.find("div",class_="product_price")
    price=prod.find("p",class_="price_color")
    products.append(
        {
            "Title":title.strip(),
            "Price":price.text.replace("Â£","")
        }
    )
print(*products,sep="\n")
```

### Sample Scraping for Books(with next)

```python
from bs4 import BeautifulSoup
import requests

header={"User-Agent":"Mozilla/5.0"}
base_url="https://books.toscrape.com/"
next_url="catalogue/page-1.html"
i=1
products=[]
while next_url and i<3:
    curr_url=base_url+next_url
    html=requests.get(curr_url,headers=header)
    soup=BeautifulSoup(html.text,"html.parser")
    articles = soup.find_all("article", class_="product_pod")
    for li in articles:
        h3=li.find("h3")
        a=h3.find("a")
        title=a.get("title")
        prod=li.find("div",class_="product_price")
        price=prod.find("p",class_="price_color")
        products.append(
            {
                "Title":title.strip(),
                "Price":price.text.replace("Â£","")
            }
        )
    is_next=soup.find("li",class_="next")
    if is_next:
        next_url="catalogue/"+is_next.find("a")["href"]
    else:
        next_url=None    
    i+=1
print(*products,sep="\n")
```


## Selenium

**Selenium** is an open-source tool used for **automating web browsers**. It supports multiple programming languages and browsers, making it a popular choice for automated testing of web applications.

#### Supported Programming Languages

- Java (most widely used)
- Python
- JavaScript (Node.js)
- C#
- Ruby

####  Supported Browsers

- Chrome (via ChromeDriver)
- Firefox (via GeckoDriver)
- Edge (via EdgeDriver)
- Safari (macOS only)


