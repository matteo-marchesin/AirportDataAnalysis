# -*- coding: utf-8 -*-
"""
script to scrap data from flightradar24
Created on Thu Aug  8 14:12:01 2019
@author: matteo_marchesin
"""

#import libraries
import pandas as pd
import flightRadar24_scrapping as fRs
from selenium import webdriver
from datetime import date
import airport_data as ad



#root-url and system path folder declarations

_url ='https://www.flightradar24.com/data/airports/' 
#gecko_path = r'...'
#data_folder = r'...'

gecko_path = r'...'
data_folder = r'...'


    #webDriver options
options = webdriver.FirefoxOptions()
options.add_argument('--ignore-certificate-errors')
options.add_argument('--incognito')
options.add_argument('--headless')
browser = webdriver.Firefox(executable_path = gecko_path,firefox_options = options)
browser.implicitly_wait(200) # seconds
##############################################################################

'''
input =  url, airport name
output = airport dataset for departures and arrivals

''' 
for i in range(len(ad.airport_list)):
    print("ciclo i")
    browser = webdriver.Firefox(executable_path = gecko_path,firefox_options = options)

    dept_df,arrv_df = fRs.importData(_url, ad.airport_list[i], browser)
    
    dept_file_name = data_folder + '\\'+ ad.airport_list[i] + '\\_' + ad.airport_list[i] + '_' + 'dept_' + str(date.today())
    arrv_file_name = data_folder + '\\'+ ad.airport_list[i] + '\\_' + ad.airport_list[i] + '_' + 'arrv_' + str(date.today())

    dept_df.to_csv(dept_file_name)
    arrv_df.to_csv(arrv_file_name)
    
    browser.quit()
    del dept_df
    del arrv_df



#merging dataset with existing

#save dataset and backup copy
