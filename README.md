- 👋 Hi, I’m @Hjpwai
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Hjpwai/Hjpwai is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
# -- coding: utf-8 --** 

from telegram.ext.dispatcher import run_async 

from telegram.utils.helpers import create_deep_linked_url 

from telegram.ext.commandhandler import CommandHandler 

from telegram.ext.callbackcontext import CallbackContext 

from telegram.update import Update 

from telegram.ext.updater import Updater 

from telegram import InlineKeyboardMarkup, InlineKeyboardButton 

import re 

import linecache 

import string 

import os 

import requests 

import json 

import asyncio 

import aiohttp 

import random 

from telegram import ParseMode 

import pymysql 

from telegram.ext import Filters,MessageHandler,CallbackQueryHandler,PreCheckoutQueryHandler,ShippingQueryHandler 

from telegram import LabeledPrice, ShippingOption, Update 

from telegram import InputMediaAudio, InputMediaDocument, InputMediaPhoto, InputMediaVideo 

def aexec(func): 

def wrapper(update: Update, context: CallbackContext): 

loop = asyncio.new_event_loop() 

asyncio.set_event_loop(loop) 

loop.run_until_complete(func(update, context)) 

loop.close() 

return wrapper 

async def fetch(session, url): 

headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.131 Safari/537.36'} 

ip = 'http://127.0.0.1:7890' 

async with session.get(url,proxy=ip,headers=headers) as r: 

print(await r.json()) 

return await r.json() 

@aexec 

async def start(update: Update, context: CallbackContext): 

_= re.findall(r"(?:/start )(.+)", update.message.text) 

if len(_) > 0 : 

update.message.reply_text(text="您好，请直接向我发送数据") 

update.message.reply_text(text="您好，请直接向我发送数据") 

@aexec 

async def invite(update: Update, context: CallbackContext): 

update.message.reply_text( 

text='推廣請勿局限於TG平台,其他平台的效果同樣明顯:你可以去貼吧、微博、QQ群/空間、微信群/朋友圈、嗶哩嗶哩、Twitter、Facebook、Reddit、論壇、甚至抖音快手推廣機器人,全憑你的能力,只要你不懶就一定能推廣成功.') 

update.message.reply_text( 

text='您的专属邀请链接 \n http://t.me/f888bot?start='+ 

str(update.message.from_user.id)) 

@aexec 

async def echo(update: Update, context: CallbackContext): 

weibo = 0 

qq = 0 

phone = 0 

daqu = 0 

name = 0 

qqlm = 0 

phonediqu=0 

tag="🏷️" 

proxy = '127.0.0.1:7890' 

proxies = { 

"http": "http://%(proxy)s/" % {'proxy': proxy}, 

"https": "http://%(proxy)s/" % {'proxy': proxy} 

} 

print('from user:', update.message.from_user.id,update.message.from_user.username) 

global need 

need=update.message.text 

print(need) 

if len(need) < 2: 

context.bot.sendMessage(chat_id=update.message.chat_id, 

text='请发送正确内容') 

pass 

pattern = re.compile(r"[1-9]\d{4,10}") 

strs = need 

result_qq = pattern.findall(strs) 

pattern = re.compile(r"1[356789]\d{9}") 

strs = need 

result_phone = pattern.findall(strs) 

print(result_phone) 

if len(result_phone) > 0: 

async with aiohttp.request('GET', 'https://zy.xywlapi.cc/wbphone?phone='+str(result_phone[0])) as r: 

rt = await r.text() 

try : 

data=json.loads(rt) 

if data["status"]== 200: 

weibo=data["id"] 

except: 

pass 

async with aiohttp.request('GET', 'https://zy.xywlapi.cc/qqphone?phone='+str(result_phone[0])) as r: 

rt = await r.text() 

try : 

data=json.loads(rt) 

if data["status"]== 200: 

qq=data["qq"] 

phonediqu=data["phonediqu"] 

async with aiohttp.request('GET', 'https://zy.xywlapi.cc/qqphone?phone='+str(result_phone[0])) as r: 

rt = await r.text() 

try: 

data=json.loads(rt) 

if data["status"]== 200: 

qqlm =data["qqlm"] 

async with aiohttp.request('GET','https://zy.xywlapi.cc/qqlol?qq='+data["qq"]) as r: 

rt = await r.text() 

try: 

data=json.loads(rt) 

if data["status"]== 200: 

lolname=data["name"] 

daqu=data["daqu"] 

except: 

pass 

except: 

pass 

except: 

pass 

if len(result_qq) > 0: 

async with aiohttp.request('GET','https://zy.xywlapi.cc/qqapi?qq='+str(result_qq[0])) as r: 

rt = await r.text() 

try : 

data=json.loads(rt) 

if data["status"]== 200: 

phone=data["phone"] 

print(phone) 

phonediqu=data["phonediqu"] 

print(phonediqu) 

async with aiohttp.request('GET','https://zy.xywlapi.cc/wbphone?phone='+str(phone)) as r: 

rt = await r.text() 

print(rt) 

try: 

data=json.loads(rt) 

if data["status"]== 200: 

weibo=data["id"] 

except: 

pass 

async with aiohttp.request('GET','https://zy.xywlapi.cc/qqlm?qq='+str(result_qq[0])) as r: 

rt = await r.text() 

try: 

data=json.loads(rt) 

if data["status"]== 200: 

qqlm=data["qqlm"] 

except: 

pass 

async with aiohttp.request('GET','https://zy.xywlapi.cc/qqlol?qq='+str(result_qq[0])) as r: 

rt = await r.text() 

try: 

data=json.loads(rt) 

if data["status"]== 200: 

name=data["name"] 

daqu=data["daqu"] 

except: 

pass 

except: 

pass 

info='' 

if not len(need) < 2: 

info='🎉🎉🎉查询成功🎉🎉🎉' 

if not phone ==0: 

info=info+'\n'+tag+"数据标签: 「 手机号 」"+'\n'+'手机号：'+phone 

if not phonediqu==0: 

info=info+'\n'+tag+"数据标签: 「 运营商 」"+'\n'+"运营商："+phonediqu 

if not qq ==0: 

info=info+'\n'+tag+"数据标签: 「 qq号 」"+'\n'+"qq号："+qq 

if not weibo==0: 

info=info+'\n'+tag+"数据标签: 「 微博号 」"+'\n'+"微博号："+weibo 

if not name== 0: 

info=info+'\n'+tag+"数据标签: 「 LOL账号 」"+'\n'+"lol账号："+name 

if not daqu == 0: 

info=info+'\n'+tag+"数据标签: 「 LOL大区 」"+'\n'+"loldaqu："+daqu 

if not qqlm==0: 

info=info+'\n'+tag+"数据标签: 「 qq老密 」"+'\n'+"老密："+str(qqlm) 

print(info) 

if qqlm==0 and phone==0 and qq==0 and weibo==0 and name==0: 

if not len(need) < 2: 

update.message.reply_text(text="暂无此数据" ) 

else: 

if not len(need) < 2: 

context.bot.sendMessage(chat_id=update.message.chat_id, 

text=info) 

@aexec 

async def me(update,context) -> None: 

ed="✨" 

update.message.reply_text(text=ed+'你的用户id:'+str(update.message.from_user.id)+'\n'+ed+"chaid:"+str(update.message.chat_id)) 

def main() -> None: 

proxy = '127.0.0.1:7890' 

proxies = { 

"http": "http://%(proxy)s/" % {'proxy': proxy}, 

"https": "http://%(proxy)s/" % {'proxy': proxy} 

} 

token = "5887142012:AAF8igsf2uR8NgQI1WDT5EbDPlhuK-tmzQQ" 

updater = Updater(token=token,use_context=True,request_kwargs={'proxy_url':'socks5h://127.0.0.1:7890'}) 

dispatch = updater.dispatcher 

#updater.dispatcher.add_handler(CallbackQueryHandler(play)) 

#updater.dispatcher.add_handler(CommandHandler('settings', settings, run_async=True)) 

updater.dispatcher.add_handler(CommandHandler('me', me, run_async=True)) 

updater.dispatcher.add_handler(CommandHandler('start', start, run_async=True)) 

updater.dispatcher.add_handler(CommandHandler('invite',invite, run_async=True)) 

#updater.dispatcher.add_handler(CommandHandler('staus', staus, run_async=True)) 

#updater.dispatcher.add_handler(CommandHandler('puton_id', puton_id, run_async=True)) 

#updater.dispatcher.add_handler(CommandHandler('reload', reload, run_async=True)) 

updater.dispatcher.add_handler(MessageHandler(Filters.text, echo, run_async=True)) 

updater.start_polling() 

updater.idle() 

if __name__ == "__main__": 

main() 

mport pymysql 

import pandas as pd 

db = pymysql.connect(host='127.0.0.1', 

user='root', 

password='123456', 

database='du') 

cursor = db.cursor() 

sql = """ 

select * from weather_test 

where create_time between '2020-09-21' and '2020-09-22' 

and city in ('上海','杭州') 

""" 

cursor.execute(sql) 

cds = cursor.fetchall() 

weather = pd.DataFrame(list(cds),columns=['','时间','省份','城市','最高温度','最低温度','白天天气','夜间天气','风力','风向']) 

cursor.close() # 关闭游标 

db.close() 

import requests 

headers={ 

'accept': '*/*', 

'accept-encoding':'gzip, deflate, br', 

'accept-language': 'zh-CN,zh;q=0.9', 

'cookie': 'kg_mid=ebb2de813317a791bcf7b7d3131880c4; UM_distinctid=1722ba8b22632d-07ac0227c507a7-4e4c0f20-1fa400-1722ba8b2284a1; kg_dfid=0Q0BEI47P4zf0mHYzV0SYbou; kg_dfid_collect=d41d8cd98f00b204e9800998ecf8427e; Hm_lvt_aedee6983d4cfc62f509129360d6bb3d=1590041687,1590280210,1590367138,1590367386; Hm_lpvt_aedee6983d4cfc62f509129360d6bb3d=1590367431', 

'referer': 'https://www.kugou.com/yy/html/search.html', 

'sec-fetch-mode': 'no-cors', 

'sec-fetch-site': 'same-site', 

'user-agent': 'Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36' 

} 

aa=input('请输入歌名：') 

data={ 

'callback': 'jQuery112408716317197794392_1590368232677', 

'keyword':aa, 

'page': '1', 

'pagesize':'30', 

'userid':'-1', 

'clientver': '', 

'platform': 'WebFilter', 

'tag': 'em', 

'filter': '2', 

'iscorrection': '1', 

'privilege_filter': '0', 

'_': '1590368232679', 

} 

res = requests.get('https://www.kugou.com/yy/html/search.html',params=data) 

print(res) 

#!/usr/bin/env python3 

# -*- coding: utf-8 -*- 

import os,sys,requests 

proxy = '127.0.0.1:7890' 

proxies = { 

"http": "http://%(proxy)s/" % {'proxy': proxy}, 

"https": "http://%(proxy)s/" % {'proxy': proxy} 

} 

url = "https://suishenmafront1.sh.gov.cn/smzy/yqfkewm/relative/idcard-auth" 

headers = { 

"User-Agent":"Mozilla/5.0 (Linux; Android 12; M2012K11AC Build/SKQ1.211006.001; wv) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/86.0.4240.99 XWEB/4343 MMWEBSDK/20221011 Mobile Safari/537.36 MMWEBID/4555 MicroMessenger/8.0.30.2260(0x28001E3B) WeChat/arm64 Weixin NetType/5G Language/zh_CN ABI/arm64 miniProgram/wxc5059c3803665d9c", 

"Accept": "application/json, text/plain, */*", 

"Accept-Language": "zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7", 

"X-Requested-With": "com.tencent.mm" 

} 

data = { 

"name": "胡建", #改名字 

"id_card": "441481200710211726", 

"mw": "tChGO5otqa6EEnpLpO5bfyXgLMtLQFynXhpsSS3ZDPWi29wZbe0TuOhDMUwl3QSP6YEJKJShiBUn820KajqFDahFOCyQnr 3YRqdWy 2Pw9PzvCa GP2nm7KWFSzrrlFr/LzA2sPTCPPoRK/UvENLQ==" 

} 

code = '200' 

while 

r = requests.post(url,headers=headers,json=data,proxies=proxies).json() 

print(r)
