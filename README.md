# Shopify Google Product Ads Update Tool
This Python script uses the Shopify REST API to get all of the available products within a shop and generate files for uploading to Google Merchant Centre for Google Product Ads and Google Local Product Ads.  This script was
produced for a client that was using the Shopify Google App to implement Google Shopping Ads and found the following limitations:
- No support for Local Product Ads
- A large portion of products in Google Merchant Centre expired due to the expiration_date field not being updated by the App
- The Client wanted to limit the products included in Google Shopping ads to over a certain price point
- No easy way to add gender and age_group to Google
- Wanted a way to customise the title used for Google Shopping Ads
- Wanted to implement Microsoft Ads

Requirements
Python 3

Python Packages required
csv
requests
urllib3
pysftp
beautifulSoup4
datetime


Seup the following parameters to suit your shop

SHOP_NAME = 'xxxxxxxxx.myshopify.com'                                           #Your Shopify shop name

API_KEY = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'                                    #API Key from your private APP setup within Shopify

PASSWORD = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'                             #Password from your private APP

API_VERSION = '2020-07'                                                         #REST API Version in use

GOOGLE_SHOPPING_FEED = 'D:\Google_Shopping_Product_Feed.txt'                    #Google Shopping Feed File to upload to Google Merchant Centre

GOOGLE_LOCAL_SHOPPING_FEED = 'D:\Local_Products_Feed.txt'                       #Google Local Product Feed File to upload to Google Merchant Centre

GOOGLE_LOCAL_SHOPPING_INV = 'D:\Local_Products_Inventory.txt'                   #Google Local Products Inventory Feed File to upload to Google Merchant Centre

GOOGLE_PRODUCTCODE_CSV = 'gpc.csv'                                              #File containing mapping of Product Types in Shopify to Google Product Taxomy

GOOGLE_MERCH_ID = ''                                                            #Google Merchant ID used to identify local store

GMC_API_PW = ''                                                                 #Google merchant centre API password to upload files

GMC_API_UN = ''                                                                 #Google merchant centre API UN to upload files

COUNTRY_CODE = 'AU'                                                             #Used for Shipping purposes

STANDARD_SHIPPING_COST = '10.00'                                                #Used for setting the Standard Shipping Rate

STANDARD_SHIPPING_CURRENCY = 'AUD'                                              #Used for setting the Standard Shipping Currency

EXCLUDE_FROM_GOOGLE_SHOPPING_PRICE = 19.95                                      #Use this to exclude low value items from Google shoppping Ads, inserted item in Local Products

shopify_location_id='123456'
google_merchant_local_id='Not Used'                                             #For Local Products this must match the Google Merchant ID setup in Google Business

itemid_prefix='shopify_AU_'                                                     #Used to identify products in Google, can be set to any value as it uses Product ID and Variant ID to ensure product naming does not clash

PID_file='d:\gpc_issues.txt'                                                    #File that captures all of the product types that are not mapped to a Google Product Taxomy

included_destination = 'Shopping Ads,Display Ads,Surfaces across Google'        #Included destinations determine where your ads will appear on the Google Ads network 

excluded_destination = 'Shopping Actions'

product_limit=250                                                               #Number of products to lookup at a time Shopify sets the limit at 250, however a smaller number may make the script run faster

GOOGLE Product Taxomy
To assist with the mapping of Shopify Product_Types to Google Product Category, I have implemented a system to lookup a csv file that contains 2 columbs, the first contains the Shopify Product Code, the second contains the Google Product Category based on the Google product Taxomy located at https://support.google.com/merchants/answer/6324436?hl=en the mapping file location and name can be customise using the GOOGLE_PRODUCTCODE_CSV parameter above
