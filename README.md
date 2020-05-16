# LinkedIn Scraper
Scrapes Any LinkedIn Data

## Installation

```bash
$ pip install git+git://github.com/jqueguiner/lk_scraper
```


## Setup
### Using Docker compose
```bash
$ docker-compose up -d
$ docker-compose run lk_scraper python3
```

### Using Docker only for Selenium server
First, you need to run a Selenium server

```bash
$ docker run -d -p 4444:4444 --shm-size 2g selenium/standalone-firefox:3.141.59-20200326
```

After running this command, from the browser navigate to your IP address followed by the port number and /grid/console. So the command will be
[http://localhost:4444/grid/console](http://localhost:4444/grid/console).


## Retrieving Cookie

### Browser-Independent:
    Navigate to LinkedIn.com and log in
    Open up the browser developer tools (Ctrl-Shift-I or right click -> inspect element)
![https://www.nextscripts.com/images/sc/alt-LI-002-ch.png](https://www.nextscripts.com/images/sc/alt-LI-002-ch.png)
![https://i.stack.imgur.com/pVMyz.png](https://i.stack.imgur.com/pVMyz.png)

### Chrome:
    Select the Application tab
    Under the Storage header on the left-hand menu, click the Cookies dropdown and select www.linkedin.com
    Find the li_at cookie, and double click the value to select it before copying

### Firefox:
    Select Storage tab
    Click the Cookies dropdown and select www.linkedin.com
    Find and copy the li_at value



## Setting up the cookie
### Method 1 : Setting the cookie in the config file
You can add your LinkedIn li_at cookie in the config file that is located in your home (~/.lk_scraper/config.yml)
see
![https://github.com/jqueguiner/lk_scraper/raw/master/config_yaml.png](https://github.com/jqueguiner/lk_scraper/raw/master/config_yaml.png)

## Method 2 : Setting the cookie at the Scraper level
```python
from lk_scraper import Scraper
li_at = "My_super_linkedin_cookie"
scraper = Scraper(li_at=li_at)
```

## Method 3 : Using Variable Environment
(Not implemented Yet)
```bash
$ export LI_AT="My_super_linkedin_cookie"
```

## A full working example
Run the Jupyter notebook linkedin-example.ipynb


## Usage

```python
from lk_scraper import Scraper
scraper = Scraper()
```

### Company Scraping

```python
from lk_scraper import Scraper
scraper = Scraper()
company = scraper.get_object(object_name='company', object_id='apple')
```

### Profil Scraping

```python
from lk_scraper import Scraper
scraper = Scraper()
profil = scraper.get_object(object_name='profil', object_id='jlqueguiner')
```

