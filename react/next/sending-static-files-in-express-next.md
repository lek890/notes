**Serve static files from NextJs-Express app**

Generally, a next - express app would be serving dynamic pages of what your app is intended to serve. For example, on a
e-commerce site, it would a page which gives a list of products - say items categorized as kitchen, living room etc.

However there could be another case that we wanted to serve some files with static data. For example, this could be the 
files related to SEO. Say, i need some files called robots.txt and sitemap_index.xml to be available on paths relative
to the base url. 

To solve this, we could use the `static` api of express. To do this, you would need to configure your express app with 
the folders that you are going to open as public for static access. So if you set a folder called `public` as your static
folder in your express app, then you can access anything inside the public folder using relative paths. For example, you could
retrieve

```
public
    ---all-cats.txt
    ---/images
      .../cat-pic.jpeg
    ---/notes/cats
        .../cat-notes.txt
```   
as
      
abc.com/all-cats.txt
abc.com/images/cat-pic.jpeg
abc.com/notes/cats/cat-notes.txt

To acheive this you can use
`app.use(express.static( folder_name ))` to configure your app when starting the application.

ex: 
```
app.use( express.static('public') )
```
if you have internationalization, then you can even do

```
app.use( express.static(`public/${YOUR_REQUIRED_FOLDER}`) )`
```

In some cases, the urls to retreive the files may not be the same as the file name. For example, the sitemaps_index.xml may
have to be retrieved from a url `abc.com/sitemaps`. In that case, you could achieve this by checking the url and sending
the files. This could be in any of the middlewares you use or could be in one of the static pages you have in your `pages` 
directory where you have access to the response object.

Simply put, if my url is `sitemaps`

```
if ( asPath.match(/sitemaps/i)){
  const options = { //set your header options here }
  res.sendFile('sitemaps_index.xml', options)
}
```

there is a callback option available if you need to do error handling
```
if ( asPath.match(/sitemaps/i)){
  const options = { //set your header options here }
  res.sendFile('sitemaps_index.xml', options, (err) => console.log('some error occured', err))
}
```

Read more here :
- https://expressjs.com/en/starter/static-files.html
- http://expressjs.com/en/5x/api.html#res.sendFile

