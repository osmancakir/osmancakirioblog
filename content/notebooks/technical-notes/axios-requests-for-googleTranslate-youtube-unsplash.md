---
title: "Get Requests with Axios for Google Translate, Youtube and Unsplash"
author: "Osman Cakir"
date: 2020-09-30T06:53:49-07:00
description: "An article about building axios api requests for different apis."
type: technical_note
draft: true
---


Hi There, 

Up until now we have made 3 different api calls for 3 different apis. 

- Unsplash

- Youtube

- Google Translate. 

When I compare the documentation of these apis and the axios requests we coded, I don't get a clear picture. I also looked at axios documentation and didn't find the source I am looking for. 

## For Unsplash: 

```javascript
 onSearchSubmit = async (term) => {
    const response = await axios.get("https://api.unsplash.com/search/photos", {
      params: { query: term },
      headers: {
        Authorization: "Client-ID dlB_zLoLKThdFSN5B0L6CMvnbLq8c-Ybw4X3ViiJz9I",
      },
    });
    console.log(response.data);
    this.setState({ images: response.data.results });
  };
```

## For Youtube: 

```javascript
 onTermSubmit = async (term) => {
    const response = await axios.get("https://www.googleapis.com/youtube/v3/search", {
      params: {
        part: "snippet",
        type: "video",
        maxResults: 5,
        q: term,
        key: KEY,
      },
    });
    this.setState({ videos: response.data.items, selectedVideo:response.data.items[0] }); // to prevent selected video to stick : 129
  };


```

## For Google Translate
```javascript

    useEffect(() => {
        axios.post('https://translation.googleapis.com/language/translate/v2', {}, {
            params: {
                q: text,
                target: language.value,
                key: 'AIzaSyCHUCmpR7cT_yDFHC98CZJy2LTms-IwDlM'
            }
        })
    }, [language,text])

```