# cross
'Cross' a live data tool for migrants crossing the Mediterranean Sea between Libya and Italy.

[Live](http://cross.fromscratch.io/)

![migrants](https://timedotcom.files.wordpress.com/2017/08/italy-migrants.jpg)

### Why
'cross' is a live data tool that lets migrants know if it is relatively safe to cross or not cross the sea between Libya and Italy.
It is constantly updated and it generates a simple outcome, ‘cross’ or do ‘not cross' based on data from UNHCR and IOM. Data analysis allows migrants to know how deadly the route has been for the current year at the present state. A risk index is generated based on how and if mortality rate is higher or lower than the historical yearly average.
It is a project that flips the common structure in data studies. While we are constantly analized over the internet, rarerly these information we produced, become tools that we can use for our decisions. Here the migrants are the data and they are also the ones using them back.

### What
Signals should give us timely right answers to our questions. Think about a traffic light.
Unfortunately, there’s no such a thing as the right time to cross a sea for a migrant, even if this includes make the deadliest crossing in the world. Since 2014, more than 14,000 people are dead or missing in the central Mediterranean. Despite these dramatic numbers, no data or analysis seems able to create enough awareness to stop this massacre. Over time another paradox has appeared: the analysis that come from these migrants, are not designed for them. What if migrants can use their own data?
‘cross’ oversimplified structure strikes as warning and provocation. A provocation against the simplified and post-factual narrative about what it's truly happening. A warning to the misuse of data analysis. 'cross' is call to action to converge into a compelling narrative that aims to save human lives by directly helping the migrants while raising awareness around the limits of a purely data driven public narrative.

### How
The aim of this project is not built a fully reliable decision model, it is to create awareness around the loss of human lives of the largest migration in Europe since 1945 and the recent 'zero-landing' policy applied by Italy.
Using official data available since 2014 for the central Mediterranean route, the historical yearly average mortality rate (dead or missing people/number of arrivals) has been compounded for the last three years. If the current death rate is lower than the 2014-17 average, the output is 'cross' and vice versa. The risk index is compound as how different is the real time mortality rate compared to the past in percentage. Since many factors beyond these data can make a substantial difference in the safety of the journey, we do not encourage migrants to base their decision on our data alone.
Data sources: UNHCR, IOM.

## Behind the hood
The entire model has centered on purpose to be radically simple and straightforward. The key metric set was mortality rate. In this case, this rate is: deaths or missing migrants/arrivals. Retrieving data to compound it, has been more challenging than expected.
Two main intergovernmental organizations collect and provide data to all other stakeholders including newspaper: UNHCR and International Organization for Migration (IOM). UNHCR provides a basic API but unfortunately doesn't look particularly updated. As matter of fact some calls do not work at all. UNHCR data lack of granularity when it comes to compound the number of deaths. On the other hand, IOM does a great job in collecting information about mortality in the Mediterranean sea with the Missing Migrant Project. Unfortunately, IOM doesn't provide any API framework.

From a data standing point, this project has been developed using:
A. [API from UNHCR](http://data2.unhcr.org/en/situations/mediterranean/location/5205) to get the number of arrivals in Italy.
B. [IOM data](http://missingmigrants.iom.int/mediterranean) to get the number of deaths and missing migrants.

Since IOM doesn't have an API, I had to implement client-side web scraping. This source ([Client-side web scraping with JavaScript using jQuery and Regex](https://medium.freecodecamp.org/client-side-web-scraping-with-javascript-using-jquery-and-regex-5b57a271cb86)) has been particularly useful. CORS problem emerged has my requests were made to IOM's url to scrape its page.

#### Why client-side web scraping?
I've personally felt in love with a amazing tool developed by [Astroshock](http://astroshock.ru/) in Moscow kindly suggest by the award-winning designers duo [Anton&Irene](http://antonandirene.com/) which I had the chance to collaborate with in the past: [Readymag](https://readymag.com/).
I think Readymag is the Ferrari of MVP production on the web. It's much more than a website builder or worse a portfolio builder. It's intuitive, well designed and with a great selection of in-house tools to design amazing professional website. The quality and quantity of animations and how fast it's easy to implement them, it's remarkable.
The first draft of 'Cross' was created on Readymag and it was static. Using the code-block, I've been able to write in Javascript with Jquery and Regex the scraping method and the API call to get the data.
Even if there's an inherent lack of flexibility on the backend, the front-end developed is truly fast.
