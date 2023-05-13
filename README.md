# Emailscraped
from bs4 import BeautifulSoup
import requests
import requests.exception
import urlib.parse
from collection import deque
import re

 user_url=str(input('[+]Enter Target url to scan'))
 urls = deque([user_url])

 scrapped_url= set()
 email= set()

 count =0
 try:
 while len(urls):
 count += 1
 if count ==10
 break
 url =url.popleft()
 scrapped_url.add(url)

 parts=urllib.parse.urlsplit(url)
 base_url  '{0.scheme}'://'{0.scheme}' , format(parts)

 path=url[:url.rfind(/'')+1] if '/' in parts.path else url
 print('[%d]Processing %s' % (count , url))

 try:
 response = request.get(url)

 expect(request.execption.MissingSheme, requests.exceptions,ConnectionError):
 continue
  new_emails =set(re.findall(r'[a-z0-9\. \-+_]+@[a-z0-9\. \-+_]+\.[a-z]+', response.text,re.I))

  emails.update(new_emails)

  soup = BeautifulSuop(response.text, features="lxml")

  for anchor in soup.findall("a")
  link = anchor.attrs['herf'] if 'herf' in anchor.attrs else ''
  link = base_url+ link
  elif not link.startsswitch('htttp'):
  link = path+ link
  if not link in urls and not link in scraped_urls:
  urls.apped=nd(link)

  expect Keboarddinterrupt:
  print('[-]Closing!')

  for mail in emails:
  print(mail)
