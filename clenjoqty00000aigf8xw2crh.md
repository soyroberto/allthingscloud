---
title: "How my Spotify Music looks in PowerBI"
datePublished: Tue Feb 28 2023 01:03:07 GMT+0000 (Coordinated Universal Time)
cuid: clenjoqty00000aigf8xw2crh
slug: how-my-spotify-music-looks-in-powerbi
tags: spotify, powerbi, office365

---

# Music is life;

![](https://qzvodq.bn1304.livefilestore.com/y4m6oIwdj0uiqJmFS8Sc48NL8Umetkt3zVewr1gJvhNwp7yXFdmTzDzYL-pA1decO8TfHo5iKdwAb3tE2h9oeESCkwdhlK3FcY4l208XfT3Eir-MD1CTXufGfAj_PxbXBvdI8780pXb7zp0Xa9IQUSAK8F7xr_Pig0RzS9u2HYHYRR73sjOyDaXaB9dk_Jp4I4ylPDlPbJmar74hl1fU6eaeQ?width=1000&height=1000&cropmode=none align="left")

I love music, there's no single day that passes by that I don't listen to music, I need music, like right now, I'm listening to **Kraftwerk's** song ***The Robots***, fantastic song and when I get to work and when I travel and when I have dinner at home, music is air for me.

I dream, sleep, eat, walk and work with music, not a genre in specific. I can be very varied in my taste, I do have a natural tendency in terms of popular music towards the 80's and 90's because I was a kid when Michael Jackson's Thriller came out.

Also, I do love Classical especially the Romantics and Soundtracks, for example, I've been listening to the Bladerunner soundtrack, fantastic.

In today's world, anyone can listen to anything on demand, gone are the days of buying the album, and having to wait for it, not today, anything is available on the spot. With the multiple services available: Pandora, Spotify, Apple Music, YouTube and many others.

The music service I use is Spotify and for the most part, I like it, some hassles here and there but it does good work. They provide a REST API to interact with the internals of their platform. More details of it, [here](https://developer.spotify.com/web-api/).

As I was browsing their API I found that I can get the songs and genres I listen and I've listened to. I then came up with an idea! What if I picture my music data with PowerBI? How would it look?

## The Extraction

***Get User's Top Artists and Tracks***[here](https://developer.spotify.com/web-api/console/get-current-user-top-artists-and-tracks/)

```plaintext
curl -X GET "https://api.spotify.com/v1/me/top/artists?time_range=long_term&limit=50" -H "Accept: application/json" -H "Authorization: Bearer BQCsk6TFcNqCPZodC13lPp82G1kJ6MZz203PwGrbI1u
```

This is how it looks:

![](https://lhqipq.bn1304.livefilestore.com/y4mX2RCCrG9vkVAbshi5ASnIab5ft6MZxk2mZLp7eTJW3k_v7D5MeKemoFsV765yeeXFDuNM9nUiqJTqk38V0I-66MaZ-5LgDzKawfcnO_mQRPckp5g3ZumLZh_DSaCfpvssmPWi7k0M1KiZ9MOx7jcUghK9ypaj0b311H2WQZdz6McsuFXJh28gxIGWvhhZr7ZR2MQUAxmIpkO-8tU5rd5Gg?width=2558&height=826&cropmode=none align="left")

And certainly I needed to do some massaging of the data:

1. It outputs in JSON
    
2. Which I then converted to CSV
    
3. Which I then import into Excel for cleansing, removed the not necessary columns
    
4. And then Imported to PowerBI for visualising
    

## The Graphics

**Page 1**. My historical listening patterns grouped by Genre with the corresponding Artist(s). My most listened genre is Alternative Dance with eleven artists, next are Adult Standards and Alternative Rock and so on.

Another important number is how high the artist is on my list, The Cocteau Twins is my #1 listened artist and Depeche Mode is number 2, etc. This data should go back all the way to when I started to use Spotify, back in May of 2012 when they launched the service in Australia.

**Page 2.** Grouped by Genre in alphabetical order, showing the artist(s) and their Spotify Ranking. In Alternative Dance which is my most listened genre.

<iframe width="933" height="700" src="https://app.powerbi.com/view?r=eyJrIjoiY2E1NTg3MmYtNGNmOC00MzExLThkMGItNjZlMDZhYmZkYWQ1IiwidCI6Ijk2NTVmOWNiLTI2MDUtNGNkYS05M2U0LTc3YmJkODg5ZmQ2NiIsImMiOjR9"></iframe>

Seeing this data confirms my music patterns that I practice every day automatically, having access to it and being able to create graphics out of it is fantastic.

There are other  ways to create and show graphics with PowerBI. Like thes ones below:

**Page 1:** In Alphabetical Order

**Page 2**: In Alphabetical Order with a number in each square showing how popular the song was for me when I ran the report.

**Page 3**: In alphabetical order, showing: Number of songs I listened from that artist, how popular the artist is on my list and on Spotify

**Page 4**: Showing number of songs and each song with its popularity number both for me and on Spotify. Clearly two artists took the most listening Slowdive and Polo y Pan.

<iframe width="933" height="700" src="https://app.powerbi.com/view?r=eyJrIjoiZjIwZjMxZWYtMDBhZS00YzMzLWFiYjAtYmI2ZjU5ZWVhNjdhIiwidCI6Ijk2NTVmOWNiLTI2MDUtNGNkYS05M2U0LTc3YmJkODg5ZmQ2NiIsImMiOjR9"></iframe>

Roberto