library("xml2")
library("rvest")
library("dplyr")
library("stringr")
library("rlist")

url = c("https://pjsekai.com/?aad6ee23b0")
web = read_html(url, encoding = "UTF-8")
song_title = web%>%html_nodes("tr")%>%html_text();a
song_title = song_title[29:380];song_title
song_title = song_title[1:332];song_title

song_title = gsub("\\_.*", "", song_title);song_title
song_title = gsub(".*既","",song_title);song_title
song_title = gsub(".*書","",song_title);song_title
song_title = gsub(".*公","",song_title);song_title
song_title[26] = c("悔やむと書いてミライ")
song_title
song_title = gsub(" ","",song_title);song_title
song_title = gsub('.{1}$', '', song_title);song_title
song_title[311] = c("悪徳のジャッジメント")
song_title[329] = c("太陽系デスコ")

len = nchar(song_title)

song_data = data.frame(song_title = song_title,len = len);song_data

song_data %>% count(len)#count len
subset(song_data,song_data$len==4)