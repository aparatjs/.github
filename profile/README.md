# Aparat.JS 🌐

[![npm version](https://img.shields.io/npm/v/aparat.js.svg?style=flat-square)](https://www.npmjs.com/package/aparat.js)
[![Downloads](https://img.shields.io/npm/dm/aparat.js.svg?style=flat-square)](https://npm-stat.com/charts.html?package=aparat.js)
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](https://github.com/Sobhan-SRZA/aparat.js/blob/main/LICENSE)

A powerful Node.js wrapper for the Aparat video platform (Iranian YouTube alternative) providing seamless access to user profiles, video data, and live stream monitoring.

## 📦 Installation

```bash
npm install aparat.js
# or
yarn add aparat.js
```

## 🚀 Features

- **User Profile Analysis**: Get detailed channel statistics
- **Video Metadata**: Retrieve comprehensive video information
- **Live Stream Monitoring**: Real-time stream status tracking
- **Advanced Search**: Find users and videos with precision
- **TypeScript Ready**: Full type definitions included
- **Rate Limiting Handling**: Built-in request throttling

# 📚 Documentation

## How get user profile?
An example to how catch user information like followers count and etc:
```js
const { Aparat } = require("aparat.js");
const aparat = new Aparat();
(async () => {

    // User information results.
    const user = await aparat.user.getProfile("shervinbdndev");
    console.log(`Followers: ${user.followers.toLocaleString()}`); // Returns number: 4 
    console.log(`Followings: ${user.followings.toLocaleString()}`); // Returns number:  2

})();
```

- User object results:
```json
{
 "description": "سلام به کانال من خوش آمدید.\r\nدنبال کردن یادتون نره . \r\nلطفاً نظر هايتان در ويديو های ما ارسال کنید. این کار بزرگترین حمایت حساب میشه؛)\r\nثبت نظر=دنبال کردن\r\nدنبال کردن=دنبال کردن",
 "created_at": "2018-09-01T00: 00: 00.000Z",
 "followers": 554,
 "followings": 42,
 "total_video": 91,
 "total_views": 457700,
 "month_views": 11,
 "is_forkids": false,
 "is_banned": false,
 "is_official": false,
 "user": {
  "id": 5444865,
  "name": "Action Club",
  "username": "sobhanSRZA",
  "hash_id": "1cf00f0ef4c170a243471992798a1fbf63b2f6cb",
  "icon": "https: //www.aparat.com/public/public/aparat/img/global/avatar-is-channel.png"
 },
 "links": {
  "telegram": "http://www.telegram.me/SobhanSRZA",
  "instagram": "http://www.instagram.com/srza._.action",
  "website": "https://m.youtube.com/channel/UCPR2g_2s6rR7X3zQwXVjBcw"
 }
}
```

- User object type data:
```typescript
interface Profile {
 description: string,
 created_at: Date,
 followers: number,
 followings: number,
 priority?: string,
 total_video: number,
 total_views: number,
 month_views: number,
 is_forkids: boolean,
 is_banned: boolean,
 is_official: boolean,
 user: {
  name: string,
  username: string,
  id: number,
  hash_id: string,
  icon: string,
  cover?: string,
  links?: {
   website?: string,
   twitter?: string,
   instagram?: string,
   telegram?: string,
   facebook?: string
  }
 }
}
```

---

## How search a video?
```js
const { Aparat } = require("aparat.js");
const aparat = new Aparat();
(async () => {
    // Searched vidoe results.
    const videos = await aparat.video.search("SpongBob");
    const video = videos[0];
    console.log(video.url); // Returns: https://www.aparat.com/v/eHEjW
})();
```

- Results of video search method is an array like the exmple:
```json
[
  {
    "id": 54992465,
    "hash_id": "n4163y7",
    "title": "بازی ترسناک باب اسفنجی در راک باتم سم کوتاه ! Spongbob Day of Terror",
    "description": "برای دلگرمی بیشتر لطفا هم زنگوله ویدیورو فعال کنید هم شبکه های اجتماعی دنبال کنید عشقید\n\nساعت استریم : هرشب ساعت 9 تا 12 در سایت آپارات\nویدیو جدید کانال هر روز ساعت 9 صبح اپلود میشه\n\nروبینو https://www.rubika.ir/ripbroadcast \nروبیکا https://www.rubika.ir/ripbroadcast11\nیوتیوب www.youtube.com/ripbroadcast\nدیسکوردwww.discord.gg/c4kXV5RHsw\nتوییچ www.twitch.tv/ripbroadcast\nتلگرام t.me/ripbroadcast\nاینستاگرام www.instagram.com/ripbroadcast\nحمایت مالی www.sibmo.ir/ripbroadcast\n\nتگ :\nعمو امیر\nRipbroadcast\nگیم پلی\n",
    "url": "https://www.aparat.com/v/n4163y7",
    "views": 64103,
    "likes": 5287,
    "duration": 428,
    "thumbnail": "https://static.cdn.asset.aparat.com/avt/54992465-7970-l__4352.jpg?width=900&quality=90&secret=pNq7PpNOky1WgplrE93-Kw",
    "preview": "https://static.cdn.asset.aparat.com/avt/54992465_15s.mp4",
    "frame": "https://www.aparat.com/video/video/embed/videohash/n4163y7/vt/frame",
    "publish_at": "1970-01-01T12:10:25.800Z",
    "uploader": {
    "id": "3921056",
    "name": "Rest in Peace",
    "username": "rest_in_peace",
    "icon": "https://static.cdn.asset.aparat.com/profile-photo/3921056-851567-m.jpg",
    "is_official": true
    }
  },
  ...
]
```

- Results of single video information:
  - json data:
```json
{
  "id": 54992465,
  "hash_id": "n4163y7",
  "title": "بازی ترسناک باب اسفنجی در راک باتم سم کوتاه ! Spongbob Day of Terror",
  "description": "برای دلگرمی بیشتر لطفا هم زنگوله ویدیورو فعال کنید هم شبکه های اجتماعی دنبال کنید عشقید\n\nساعت استریم : هرشب ساعت 9 تا 12 در سایت آپارات\nویدیو جدید کانال هر روز ساعت 9 صبح اپلود میشه\n\nروبینو https://www.rubika.ir/ripbroadcast \nروبیکا https://www.rubika.ir/ripbroadcast11\nیوتیوب www.youtube.com/ripbroadcast\nدیسکوردwww.discord.gg/c4kXV5RHsw\nتوییچ www.twitch.tv/ripbroadcast\nتلگرام t.me/ripbroadcast\nاینستاگرام www.instagram.com/ripbroadcast\nحمایت مالی www.sibmo.ir/ripbroadcast\n\nتگ :\nعمو امیر\nRipbroadcast\nگیم پلی\n",
  "url": "https://www.aparat.com/v/n4163y7",
  "views": 64103,
  "likes": 5287,
  "duration": 428,
  "thumbnail": "https://static.cdn.asset.aparat.com/avt/54992465-7970-l__4352.jpg?width=900&quality=90&secret=pNq7PpNOky1WgplrE93-Kw",
  "preview": "https://static.cdn.asset.aparat.com/avt/54992465_15s.mp4",
  "frame": "https://www.aparat.com/video/video/embed/videohash/n4163y7/vt/frame",
  "publish_at": "1970-01-01T12:10:25.800Z",
  "uploader": {
   "id": "3921056",
   "name": "Rest in Peace",
   "username": "rest_in_peace",
   "icon": "https://static.cdn.asset.aparat.com/profile-photo/3921056-851567-m.jpg",
   "is_official": true
  }
}
```

  - types:
```typescript
interface SearchVideo {
 id: number;
 hash_id: string;
 description: string;
 title: string;
 url: string;
 views: number;
 likes: number;
 duration: number;
 thumbnail: string;
 preview?: string;
 frame: string;
 publish_at: Date;
 uploader: {
  id: string;
  name: string;
  username: string;
  icon: string;
  is_official: boolean;
 };
}
```

---

## How get the information from video?
```js
const { Aparat } = require("aparat.js");
const aparat = new Aparat();
(async () => {
    // Get vidoe information by hash id.
    const video = await aparat.video.get("n4163y7");
    console.log(video.url); // Returns: https://www.aparat.com/v/eHEjW
})();
```

- Results of video information:
```json
{
 "id": 54992465,
 "hash_id": "n4163y7",
 "title": "بازی ترسناک باب اسفنجی در راک باتم سم کوتاه ! Spongbob Day of Terror",
 "duration": 428,
 "views": 64103,
 "thumbnail": "https://static.cdn.asset.aparat.com/avt/54992465-7970-l__4352.jpg?width=900&quality=90&secret=pNq7PpNOky1WgplrE93-Kw",
 "publish_at": "1970-01-01T12:10:26.204Z",
 "description": "برای دلگرمی بیشتر لطفا هم زنگوله ویدیورو فعال کنید هم شبکه های اجتماعی دنبال کنید عشقید\n\nساعت استریم : هرشب ساعت 9 تا 12 در سایت آپارات\nویدیو جدید کانال هر روز ساعت 9 صبح اپلود میشه\n\nروبینو https://www.rubika.ir/ripbroadcast \nروبیکا https://www.rubika.ir/ripbroadcast11\nیوتیوب www.youtube.com/ripbroadcast\nدیسکوردwww.discord.gg/c4kXV5RHsw\nتوییچ www.twitch.tv/ripbroadcast\nتلگرام t.me/ripbroadcast\nاینستاگرام www.instagram.com/ripbroadcast\nحمایت مالی www.sibmo.ir/ripbroadcast\n\nتگ :\nعمو امیر\nRipbroadcast\nگیم پلی\nترسناک\nخنده دار\nترسناک\nباحال\nبازی خنده دار\nRec Room\nبازی Rec Room\nبازی رک روم\nبازی سمی\nپارکور باب اسفنجی\nبازی ترسناک\nسایلنت هیل\nبازی پی تی\nبازی سایلنت هیل پی تی\nsilent hill pt\nsilent hill\npt\nبازی pt\nماینکرفت\nجی تی ای\nبازی ترسناک گرنی\nبازی ایرانی قتل در کوچه های تهران 2\nقتل در کوچه های تهران 2\nبازی قتل در کوچه های تهران 2\nبازی ایرانی\nبازی ترسناک باب اسفنجی\nباب اسفنجی\nبازی ترسناک\nباب اسفنجی در راک باتم\nبازی باب اسفنجی در راک باتم\nSpongbob Day of Terror",
 "frame": "https: //www.aparat.com/video/video/embed/videohash/n4163y7/vt/frame",
 "likes": 5287,
 "tags": [
  {
   "name": "بازی ترسناک باب اسفنجی",
   "video_cnt": "56"
  },
  {
   "name": "Spongbob Day of Terror",
   "video_cnt": "1"
  },
  {
   "name": "بازی Spongbob Day of Terror",
   "video_cnt": "1"
  },
  {
   "name": "باب اسفنجی در راک باتم",
   "video_cnt": "1"
  },
  {
   "name": "بازی باب اسفنجی در راک باتم",
   "video_cnt": "1"
  },
  {
   "name": "بازی Spongbob Day of Te",
   "video_cnt": "1"
  },
  {
   "name": "بازی باب اسفنجی در راک",
   "video_cnt": "1"
  }
 ],
 "url": "https: //www.aparat.com/v/n4163y7",
 "uploader": {
  "id": 3921056,
  "name": "Rest in Peace",
  "username": "rest_in_peace",
  "icon": "https://static.cdn.asset.aparat.com/profile-photo/3921056-851567-m.jpg"
 },
 "is_download_able": true,
 "download_link": "https://persian9.asset.aparat.com/aparat-video/05d291102f21cf69f5d920c544fab12454992465-1080p.apt?wmsAuthSign=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6ImFkMTAxZThjN2NjZDg0ZjM3YjEzOGIwNmJkZjUxZDBjIiwiZXhwIjoxNzM5ODk2Mjk1LCJpc3MiOiJTYWJhIElkZWEgR1NJRyJ9.xTU1MzvSFwcKmJZ4PIk2QEUTOaXPKENVFusFivJ_-Kw",
 "download_links": [
  {
   "quality": "144p",
   "url": "https://persian9.asset.aparat.com/aparat-video/05d291102f21cf69f5d920c544fab12454992465-144p.mp4?wmsAuthSign=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6IjRhOTViZTY1NWEwMDI4NzcyMjcyODM1ZGUyM2YxYjk5IiwiZXhwIjoxNzM5ODk2Mjk1LCJpc3MiOiJTYWJhIElkZWEgR1NJRyJ9.GRs9RyGesYEhnXDWsnm7XACl5LihTtjHIi2URDuZnFM"
  },
  {
   "quality": "240p",
   "url": "https://caspian8.asset.aparat.com/aparat-video/05d291102f21cf69f5d920c544fab12454992465-240p.mp4?wmsAuthSign=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6IjRhOTViZTY1NWEwMDI4NzcyMjcyODM1ZGUyM2YxYjk5IiwiZXhwIjoxNzM5ODk2Mjk1LCJpc3MiOiJTYWJhIElkZWEgR1NJRyJ9.GRs9RyGesYEhnXDWsnm7XACl5LihTtjHIi2URDuZnFM"
  },
  {
   "quality": "360p",
   "url": "https://persian9.asset.aparat.com/aparat-video/05d291102f21cf69f5d920c544fab12454992465-360p.mp4?wmsAuthSign=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6IjRhOTViZTY1NWEwMDI4NzcyMjcyODM1ZGUyM2YxYjk5IiwiZXhwIjoxNzM5ODk2Mjk1LCJpc3MiOiJTYWJhIElkZWEgR1NJRyJ9.GRs9RyGesYEhnXDWsnm7XACl5LihTtjHIi2URDuZnFM"
  },
  {
   "quality": "480p",
   "url": "https://caspian8.asset.aparat.com/aparat-video/05d291102f21cf69f5d920c544fab12454992465-480p.mp4?wmsAuthSign=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6IjRhOTViZTY1NWEwMDI4NzcyMjcyODM1ZGUyM2YxYjk5IiwiZXhwIjoxNzM5ODk2Mjk1LCJpc3MiOiJTYWJhIElkZWEgR1NJRyJ9.GRs9RyGesYEhnXDWsnm7XACl5LihTtjHIi2URDuZnFM"
  },
  {
   "quality": "720p",
   "url": "https://caspian8.asset.aparat.com/aparat-video/05d291102f21cf69f5d920c544fab12454992465-720p.mp4?wmsAuthSign=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6IjRhOTViZTY1NWEwMDI4NzcyMjcyODM1ZGUyM2YxYjk5IiwiZXhwIjoxNzM5ODk2Mjk1LCJpc3MiOiJTYWJhIElkZWEgR1NJRyJ9.GRs9RyGesYEhnXDWsnm7XACl5LihTtjHIi2URDuZnFM"
  },
  {
   "quality": "1080p",
   "url": "https://persian9.asset.aparat.com/aparat-video/05d291102f21cf69f5d920c544fab12454992465-1080p.mp4?wmsAuthSign=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0b2tlbiI6IjRhOTViZTY1NWEwMDI4NzcyMjcyODM1ZGUyM2YxYjk5IiwiZXhwIjoxNzM5ODk2Mjk1LCJpc3MiOiJTYWJhIElkZWEgR1NJRyJ9.GRs9RyGesYEhnXDWsnm7XACl5LihTtjHIi2URDuZnFM"
  }
 ]
}
```

---

## How download a video?
```js
const { Aparat, VideoQuality } = require("aparat.js");
const aparat = new Aparat();
(async () => {
  
  // Dowload with custom quality and path
  await aparat.video.download("n4163y7", VideoQuality.P360, "./example/video.mp4");

  // Download to path "./" with 720p quality by default
  await aparat.video.download("n4163y7");
})();
```

---

## Get stream data:
You can check the user profile is it start a stream or not and will be alert to you.
In an event you can have this option and use it like the example:
```js
const { Aparat } = require("aparat.js");
const aparat = new Aparat();
aparat.events.startStreamCheck("shervinbdndev");
aparat.events.once("live_start", async (streamer) => {
console.log("User is on the stream:", streamer.url); // Returns: https://www.aparat.com/shervinbdndev/live
aparat.events.stopStreamCheck("shervinbdndev"); // Stop the trigger (Note: if you don't stop the trigger it will be spam all the time)
});
```
- Streamer object type:
```typescript
interface StreamProfile {
 url: string,
 title: string | null,
 description: string | null,
 cover: string | null,
 donate_link: string | null,
 last_start_date: string | null,
 last_end_date: string | null,
 moderators: any | null,
 vip_users: any | null,
 tag: {
  id: number | null,
  name: string | null,
  type: string | null,
  picture: string | null,
  is_game: boolean | null
 },
 category: {
  id: number | null,
  name: string | null
 },
 chat: {
  pined_message: string | null
 }
}
```

--- 

## 📜 License

MIT © [Sobhan-SRZA](https://github.com/Sobhan-SRZA) & [Persian-Caesar](https://github.com/Persian-Caesar)

---

## Contatc
 
 <div align="center">
  <a href="https://srza.ir" target="_blank">
   <img align="left" src="https://raw.githubusercontent.com/Sobhan-SRZA/Sobhan-SRZA/refs/heads/main/images/social.png" alt="Sobhan-SRZA social" width=400px>
  </a>

  <a href="https://t.me/d_opa_mine" target="_blank">
   <img alt="Telegram"
    src="https://raw.githubusercontent.com/Sobhan-SRZA/Sobhan-SRZA/refs/heads/main/images/telegram-ch.svg"
    height="30" />
  </a>

  <a href="https://t.me/Sobhan_SRZA" target="_blank">
   <img alt="Telegram"
    src="https://raw.githubusercontent.com/Sobhan-SRZA/Sobhan-SRZA/refs/heads/main/images/telegram-ac.svg"
    height="30" />
  </a>

  <a href="https://www.instagram.com/mr.sinre?igsh=cWk1aHdhaGRnOGg%3D&utm_source=qr" target="_blank">
   <img alt="Instagram"
    src="https://raw.githubusercontent.com/Sobhan-SRZA/Sobhan-SRZA/refs/heads/main/images/instagram.svg"
    height="30" />
  </a>

  <a href="https://www.twitch.tv/sobhan_srza" target="_blank">
   <img alt="Twitch"
    src="https://raw.githubusercontent.com/Sobhan-SRZA/Sobhan-SRZA/refs/heads/main/images/twitch.svg"
    height="30" />
  </a>

  <a href="https://www.youtube.com/@mr_sinre?app=desktop&sub_confirmation=1" target="_blank">
   <img alt="YouTube"
    src="https://raw.githubusercontent.com/Sobhan-SRZA/Sobhan-SRZA/refs/heads/main/images/youtube.svg"
    height="30" />
  </a>
  
  <a href="https://github.com/Sobhan-SRZA" target="_blank">
   <img alt="Github"
    src="https://raw.githubusercontent.com/Sobhan-SRZA/Sobhan-SRZA/refs/heads/main/images/github.svg"
    height="30" />
  </a>
  
  <p align="left">
   <a href="https://discord.gg/xh2S2h67UW" target="_blank">
    <img src="https://discord.com/api/guilds/1054814674979409940/widget.png?style=banner2" alt="pc-development.png">
   </a>
  </p>

  <p align="right">
   <a href="https://discord.gg/54zDNTAymF" target="_blank">
    <img src="https://discord.com/api/guilds/1181764925874507836/widget.png?style=banner2" alt="pc-club.png">
   </a>
  </p>

  <div align="center">
   <a href="https://discord.com/users/865630940361785345" target="_blank">
    <img alt="My Discord Account" src="https://discord.c99.nl/widget/theme-1/865630940361785345.png" />
   </a>
  </div>

 </div>

</div>
