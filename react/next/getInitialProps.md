**Boosting page speed with getInitialProps**

I have a next page which would render a user detail. The page has to fetch the user info from the user id in the url parameter.
The fetched data then has to be set on the page for display.

One problem observed in this is that, there was a jump of the content during the initial load attributing to the time 
when the fetch was happening. That looked not so nice.

Next provides a nice way to solve this issue through `getInitialProps`. It is an async method which gets called in the 
server side and then passes the returned variables to the render part of the page as props.

So the fetch was moved to the `getInitialProps` method and data is returned and got in the render part and set to the provider.
Voila, that improved a lot.

example:


sample next page
```
const ShowFilms: NextPage = ({ filmID, filmDetails }) => 
<Film filmID={filmID}filmDetails={filmDetails} ></Film>

ShowFilms.getInitialProps = async ({ asPath }) => {
  const id = asPath.split('')[1];
  const data = await fetch(URL, { id })
  return { filmID: id, filmDetails: data  } 
}
```
