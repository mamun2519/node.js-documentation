
# My Basic Node.js bangla Documentation




## What is Node js?
Explore:
- ১৯৯৫-২০০৯ সাল জাভাস্ক্রিপ্ট শুধু ক্লাইন্ট সাইটে ব্যবহার হত।
- ২০০৯ সালে Ryan Dahl Node js ক্রিয়েট করেন। এটি দিয়ে সার্ভারে কাজ করা যায়।
- সহজ ভাষায় নোড যে এস হলো জাভাস্ক্রিপ্ট কে সার্ভার সাইডে রান করায় অর্থাৎ সার্ভার সাইডে রান করার জন্য যেযে ফিউচার দরকার হয় , তা সাধারণত node js প্রধান করে থাকে।
- নোড যে এস তৈরি হুওয়ার পর নোড যে এস এর উপর জাভাস্ক্রিপ্ট এর থার্ড পাটি প্যাকেজ নিরভ হয়ে গেল।সেটিকে মেনেজ করার জন্য node package manager (Npm) তৈরি হলো।


## What is Module? 
Explore:
- মডিউল হচ্ছে অনেক গুলো কোডের সমষ্টি বা বান্ডিল।
-- #node.js includes three types of module
- Core modules , Local modules , Third party modules

Core module : nodejs এর নিজিস্ব মডিউল বা ফ্লাটফরম যেগুলো আছে সেগুলো হচ্ছে core modules.
নিজে থেকে তৈরি করলে local module.
থার্ড পার্টি ইউস করলে thrid party modules.


## Core modules এ যা যা আছেঃ

- http: এটির ভিতর ক্লাস মেথড যেগুলো আছে সেগুলো দিয়ে সার্ভার তৈরি করি। অর্থাৎ সার্ভার মেনেজ করার জন্য ব্যবহার করা হয়।
 
- url: url persing করার জন্য ব্যবহার করা হয়।
- Querysting: querysting মানেজ করতে ব্যবহার করা হয়।
- path: ভিবিন্ন ফাইল পুল্ডারে path গুলো মেনেজ করতে ব্যবহার করা হয়।
- fs:  ফাইলের ভিতর ডিলেট,  উপডেট একশন চালাইতে ব্যবহার করা হয়।
- Utilitis : এর বাহিরে যেগুলো রয়েছে…


## Node module server Create :
```javascript
const http = require('http');
const httpServer = http.createServer((req , res) => {
      res.end('hello World')
})

httpServer.listen(5000)
console.log('server start');
}
```
Code Explore: প্রথমে মডিউল থেকে http method টা নেব। 
সেই মডিল থেকে createServer নিয়ে এনোনিমাস ফাংশন ক্রেট করব।

server টা রান করার জন্য ভেরিবলে রেখে listen দেব। তার ভিতরে path সেড করে দেব।

 ## Request respone model
 Explore: 
 - ক্লাইন্ট সাইড থেকে সার্রভার সাইডে রিকুয়েষ্ট করা হয় সার্ভার তার এগেঞ্জ এ রেস্পন্স করে। এই পসেস টা হচ্ছে Request response model.
 - ক্লাইন্ট সাইড থেকে রিকুয়েট করতে http method er,  get, post, delete, update, put, ব্যবহার করা হয়।

- আর এসবের রেস্পন্স হিসাবে দুইটা জিনিস সার্ভার দেয়। status code or data.

## রিকুয়েষ্ট রেস্পন্স মডেল যেভাবে কাজ করেঃ

```javascript
const httpServer = http.createServer((req , res) => {
      if(req.url == '/'){
            res.writeHead(200 , {'content-type': 'text/html'})
            res.write('this is home page')
            res.end()
      }
      if(req.url == '/login'){
            res.writeHead(200 ,{ 'content-type': 'text/html'})
            res.write('this is login page')
            res.end()
      }
})

httpServer.listen(5000)
console.log('server start');
```
Code Explore :
এখানে req.url যদি হয় তার ভিতরে একটা একশন চালানো হয়েছে।
যেহেতু সার্ভার স্টেটাস কোড আর ডাটা দিবে। সেই স্টেটাচ কোড সেট করার জন্য header code সেট করতে হবে।
res.writeHead() তার ভিতরে কোড এবং কন্টেন্ট টাইপ দেব।

## Understanding http client
Explore: যাহা সার্ভারে HTTP Request পাঠায় এবং Response Receive করে,  তাকেই Http client বলে।
- Example Of HTtp Client
Axios ,
Fetch, 
Jquery ajax ,
cURL (php) ,
Volly (java) ,
Retrofit (cShark) ,
RestSharp ,

- HTTP client for Testing
PostMan, Fiddler

## Understanding package json file
Explore: Package json file হচ্ছে Application এর নথি।
এই ফাইল ক্রিয়েট করার জন্য
- npm init –y

## Node js Url module
Explore: Build-in URl model
একটা url e অনেক গুলো অংশ থাকে।
host,path,query

- একটা Url কে যেভাবে ছোট ছোট খন্ডে ভাগ করবঃ
```javascript
const server = http.createServer((req , res) =>{
      const myUrl = 'https://web.programming-hero.com/web-5/video/web-5-80-10-starting-of-a-new-journey-with-special-message'
      const objectUrl = URL.parse(myUrl , true)
      const host = objectUrl.host
      res.writeHead(200 , {'content-type': 'url/html'})
      res.write(host)
      res.end()

})
server.listen(5000)
console.log('surver Run');

```
Code Explore: প্রথমে url model রিকুয়ার করবো নোড থেকে।
যে url কে ভাগ করবো সেই url কে ভেরিবলে রাখবো।
এখন সেই url.parse() করবো তার ভিতরে Url টা বসিয়ে দেব। একটা অব্জেক্ট আকারে রিটান করব।
এখন host,  pathName , search/query ধরে রিড করতে পারব।


## File systam(fs) Module
Explore : একটা ফাইল মেনেজমেন্ট করার জন্য যা যা প্রয়োজন তা সব fs করে থাকে। অর্থাৎ একটা ফাইল ডিলেট, আপডেট ইত্যাদি করে থাকে।

fs module oparetion দুইভাবে হয়ে থাকে।
- Synchronous 
- Asynchronous 

#fs synchonus opertion তখনি চালাবো যখন কোনো ওয়েব সাইট যে কাজের জন্য কল করা হয়েছে সেই কাজ সম্পূর্ণ না হলে অন্য কোনো একশন হবে না।

#fs Asynchronous operation মাল্টিটাক্স করতে পারবে।

### Fs module operation চালাতে synchronous and asynchronous কিছু মেথড রয়েছে।


## Synchronous, Asynchronous

- When Synchronous Suitable: সিনকুনাস যেহেতু কাজ সম্পূর্ণ না হলে অন্য কোনো একশন সার্ভারে পাঠাতে পারবো না, সেই কারন ক্লাইন্ট সাইট থেকে সার্ভার সেইডে এমন রিকুয়েষ্ট পাঠাতে হবে যেটা পসেস হতে সার্ভারে কম সময় লাগে। তখন সিনকুনাস ব্যবহার করব।

 - When Asynchronous suitable:  যখন সার্ভারে রিকুয়েষ্ট করলে পসেস হতে অনেক সময় লাগে তখন এসিনকুনাস ব্যবহার করা হয়।
যেমনঃ youtube vedio uploding

## Fs module method
### Fs module essential operation Asynchronous method:
- fs.readFile(ফাইল রিড)
- fs.writeFile(ফাইল নিয়ে আসা)
- fs.rename()
- fs.exists()
- fs.unlink(ডিলেট করার জন্য)
- fs.appendFile(ফাইল এর ভিতর নতুন কিছু এড করতে)
- fs.open()
- fs.mkdir()
- fs.rmdir(এক্সজিস কোনো ফাইল কে রিনেম করতে চাইলে)
- fs.readding(ফাইল এর ভিতর যা আছে সব রিড করতে চাইলে)

### Fs module essential operation synchronous method:
- প্রতিটি মেথড এর শেষে Sync শব্ধটি আছে
- Example: fs.readFileSync()



##  Create fs file read Asynchronous
```javascript
const http = require('http');
const fs = require('fs');
const fileReadAsyn = http.createServer((req , res) =>{
      if(req.url == '/'){
            fs.readFile('home.html' ,(error , data) => {
                  res.writeHead(200 , {'content-type': 'fileRead/html'})
                  res.write(data)
                  res.end()

            })
      }
})
fileReadAsyn.listen(5001)
```
## Code explore: 
First Create html file...
এখানে প্রথম fs module টা node  থেকে নেওয়া হইছে। http দিয়ে সার্ভার তৈরি করা হয়েছে।
fs.readfile এর ভিতর (৩টা ,optional shoho) দুইটা পেরামিটার যাবে। ফাইল নেইম। কলব্যাক ফাংশন। সেই কল ব্যাগ ফাংশনে দুইটা পেরামিটার যাবে। eroro হলে error হেন্ডেল করবে। data. মধ্যে ডাটা পেয়ে যাব।

##  Create fs file read Synchronous
```javascript
const http = require('http');
const fs = require('fs');
const fileReadSyn = http.createServer((req , res)=>{
      if(req.url == '/'){
            const myData = fs.readFileSync('home.html')
            res.writeHead(200 , {'content-type': "readFile/html"})
            res.write(myData)
            res.end()
      }
})
fileReadSyn.listen(5002)
```
## Code Explore:
যেহেতু synchronous অপারেশন চালালে সার্ভারে অন্য কোনো অপারেশন এক্সকিউট হবে না অন্য একশন চালানো যাবে না। তাই synchronous fs oparetion চালালে কোনো কল ব্যাক ফাংশন লাগবে না। সরাসরি ডাটা ভেরিবলে দিয়ে দেবে।



## fs file write Asynchronous
```javascript
const fileWriteAsyn = http.createServer((req , res) =>{
      if(req.url == '/'){
            fs.writeFile('text.txt' , "Hello , File write How are you?" ,(error , data) =>{
                  if(error){
                        res.writeHead(200 , {"content-type": "fileWrite/asn"})
                        res.write('File Write Fail')
                        res.end()
                  }
                  else{
                        res.writeHead(200 , {"content-type": "fileWrite/asn"})
                        res.write('File Write Success')
                        res.end()

                  }
            })
      }
})
fileWriteAsyn.listen(5003)
```
## Code Explore: 
fs থেকে writefile মেথড নেব। তার ভিতরে ৩টা পেরামিটার যাবে। ফাইল নেম। যা পাটাবো সেই ডাটা। কলবেগ ফাংশন। কলব্যগ ফংশনে একটা পেরামিটার আসবে error। 
error হলে error দেখাবো। এরর না হলে else এর ভিতর ডাটা দেখাব।


## fs file write Synchronous
```javascript
const fileWriteSyn = http.createServer((req , res) =>{
      if(req.url == '/'){
            const error = fs.writeFileSync('text.txt' , "hello , Im Sync Write file now")
            if(error){
                  res.writeHead(200 , {"content-type": 'synWrite/syn'})
                  res.write('File Write Fail')
                  res.end()
            }
            else{
                  res.writeHead(200 , {"content-type": 'synWrite/syn'})
                  res.write('File Write Success')
                  res.end()
            }
      }
})
fileWriteSyn.listen(5004)
```
## Code Explore:
সরাসরি error মধ্যে দিয়ে দেবে। কোনো কলব্যাগ ফাংশন নেই। error হলে কন্ডিশন দিয়ে
দেখাবো।

## fs file rename Asynchronous
```javascript
const reNameFile = http.createServer((req , res)=>{
      if(req.url == '/'){
            fs.rename('text.txt' , 'demo.txt' , (error) =>{
                  if(error){
                        res.writeHead(200 , {"content-type": 'synWrite/syn'})
                        res.write('File rename Fail')
                        res.end()
                  }
                  else{
                        res.writeHead(200 , {"content-type": 'synWrite/syn'})
                        res.write('File rename Success')
                        res.end()

                  }
            })
      }
})

reNameFile.listen(5005)
```
## Explore: 
প্রথমে rename মেথড টা নিতে হবে। তার ভিতরে ৩টা পেরামিটার যাবে। ১ম পেরামিটার ফাইলের পার্থ নেম। এটাকে রিনেম করার জন্য নতুন পার্থ নেম সেগেন্ড পেরামিটার হিসাবে যাবে। ৩য় পেরামিটার কলব্যাক ফাংশন।


## fs file rename Synchronous
```javascript
const renameFileSyn = http.createServer((req , res) =>{
      if(req.url == '/'){
            const error = fs.renameSync('demo.txt' , "newDemo.txt")
            if(error){
                  res.writeHead(200 , {"content-type": 'synWrite/syn'})
                        res.write('File rename Fail')
                        res.end()

            }
            else{
                  res.writeHead(200 , {"content-type": 'synWrite/syn'})
                  res.write('File rename Success')
                  res.end()
            }
      }
})

renameFileSyn.listen(5006)
```
## Code Explore:
সরাসরি error মধ্যে দিয়ে দেবে। কোনো কলব্যাগ ফাংশন নেই। error হলে কন্ডিশন দিয়ে
দেখাবো।


## fs file delete Asynchronous
```javascript

const fileDelete = http.createServer((req , res)=>{
      if(req.url == '/'){
            fs.unlink('newDemo.txt' ,(error)=>{
                  if(error){
                        res.writeHead(200 , {"content-type": 'synWrite/syn'})
                              res.write('File delete Fail')
                              res.end()
      
                  }
                  else{
                        res.writeHead(200 , {"content-type": 'synWrite/syn'})
                        res.write('File delete Success')
                        res.end()
                  }

            })
      }
})

fileDelete.listen(5007)
```
## Code Explore:
fs module প্রথমে unlink মেথড টা নিতে হবে। তার ভিতরে ৩টা পেরামিটার যাবে। ১ম পেরামিটার ফাইলের পার্থ নেম যেটিকে ডিলেট করব। ৩য় পেরামিটার কলব্যাক ফাংশন।


## fs file delete Synchronous
```javascript
const renameFileSyn = http.createServer((req , res) =>{
      if(req.url == '/'){
            const error = fs.unlinkSync('mamun.txt')
            if(error){
                  res.writeHead(200 , {"content-type": 'synWrite/syn'})
                        res.write('File Delete Fail')
                        res.end()

            }
            else{
                  res.writeHead(200 , {"content-type": 'synWrite/syn'})
                  res.write('File Delete Success')
                  res.end()
            }
      }
})

renameFileSyn.listen(5008)
```
## Code Explore:
সরাসরি error মধ্যে দিয়ে দেবে। কোনো কলব্যাগ ফাংশন নেই। error হলে কন্ডিশন দিয়ে
দেখাবো।



## fs file Exists Asynchronous
```javascript

const existsFiles = http.createServer((req , res) =>{
      if(req.url == '/'){
            fs.exists('text.txt' , (result)=>{
                  if(result){
                        res.writeHead(200 , {'content-type': "pic/html"})
                        res.write('file exist success')
                        res.end()
                  }
                  else{
                        res.writeHead(200 , {'content-type': "pic/html"})
                        res.write('file exist fail')
                        res.end()
                  }
            })
      }
})

existsFiles.listen(5009)
          
```
## Code Explore:
 প্রথমে exists  মেথড টা নিতে হবে। তার ভিতরে ৩টা পেরামিটার যাবে। ১ম পেরামিটার ফাইলের পার্থ নেম দেব যেটিকে চ্যাক করব ফাইল আছে কিনা। ৩য় পেরামিটার কলব্যাক ফাংশন।


## fs file Exists Synchronous
```javascript
     const existsFile = http.createServer((req , res) =>{
      if(req.url == '/'){
          const result =  fs.exists('text.txt')
          if(result){
            res.writeHead(200 , {'content-type': "pic/html"})
            res.write('file exists success')
            res.end()

          }
          else{
            res.writeHead(200 , {'content-type': "pic/html"})
            res.write('file exists fail')
            res.end()
          }
      }
})
existsFile.listen(5009)

existsFiles.listen(5009)
          
```
## Stream & buffers

Stream Explore:
যে ডাটা একসাথে না এসে একটু একটু করে আসে সেটিকে স্ট্রিম বলে। অর্থাৎ পার্টে পার্টে সার্ভার থেকে ডাটা পাঠানো।
যেম্নঃ ইউটিউবে বিডিও দেখা।

buffers Explore:
buffers হচ্চে যেটা আগে থেকে এসে যায় এবং সেটিকে স্টিম করে দেখায়। অর্থাৎ সার্ভার থেকে পার্টে পার্টে যে ডাটা আসে সেটিকে একটা প্যাকেট এর মত করে ফেলা।

## Note:
খন্ড খন্ড যে ডাটা আসবে সেটিকে নিয়ে কাজ করতে পারবো না। কিন্তু খন্ড খন্ড মিলে যে প্যাক্ট এর ব্যপার তৈরি হই সেটিকে নিয়ে কাজ করা যায়।

stream দুই ভাবে হয়ে থাকে
- Write strime 
- Read strime


## Read strime file read

```javascript
 const fs = require('fs');

const OurReadStream = fs.createReadStream(`${__dirname}/read.txt` , 'utf8')

OurReadStream.on('data' , (data) =>{
      console.log(data);
})
          
```

More Example: 
```javascript
const fs = require('fs');
const http = require('http');

const OurReadStream = fs.createReadStream(`${__dirname}/read.txt` , 'utf8')

const server = http.createServer((req , res) =>{
      if(req.url == '/'){
            res.write('<html><head><title>From</title></head></html>')
            res.write('<body><form method="post" action="/process"><input name="massage" type="text"></form></body>')
            res.end()
      }
      else if(req.url == '/process'){
            req.on('data' , (data )=>{
                  console.log(data.toString());

            })
            res.write('Thank You Submitting')
            res.end()
      }
})

server.listen(5000)       
```
Code Explore: 
এখানে res.on এর মাধ্যমে একটু একটু করে ডাটা এসেছে।
যদি পুরাটা আসার পর রেস্পন্স করি তাহলে even এর ভিতর data পরিবর্তে end দিতে হবে।

## Example :
```javascript
const fs = require('fs');
const http = require('http');

const OurReadStream = fs.createReadStream(`${__dirname}/read.txt` , 'utf8')

const server = http.createServer((req , res) =>{
      if(req.url == '/'){
            res.write('<html><head><title>From</title></head></html>')
            res.write('<body><form method="post" action="/process"><input name="massage" type="text"></form></body>')
            res.end()
      }
      else if(req.url == '/process'){
            const reciveBody = []
            req.on('data' , (data )=>{
                  reciveBody.push(data)
                  console.log(data.toString());

            })
            req.on('end' , (data )=>{
                  console.log('Stream Fnish');
                  const parseBody = Buffer.concat(reciveBody).toString()
                  console.log(parseBody);
            })
      }
})

server.listen(5000)       
```