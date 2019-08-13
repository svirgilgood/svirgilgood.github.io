---
layout: post
title: Zotero API
category: zotero
tags: [api, javascript, paging]
--- 

# Zotero API

[The zotero documentation isn't the
best](https://www.zotero.org/support/dev/web_api/v3/basics), but neither am I
the best reader. @textpotential helped point me to the section on Paging and
sorting, which was the key to getting the full list of Zotero's bibliography. 

Now I can page through the process by adjusting the number of results.

```
curl -X GET 'https://api.zotero.org/groups/2356093/items?limit=30&start=60' 
```


## Paging and Searching 

The two things that were missing on this post is paging and searching. You can
limit the type of records that are returned through `itemType=-attachment`
which will remove the attachments, so only bib records will be returned. 

```
https://api.zotero.org/groups/2356093/items?format=json&itemType=-attachment
```

Also, the header provides additional insights into the library and collections
as a whole. 

```
fetch('https://api.zotero.org/groups/2356093/items?format=json&itemType=-attachment')
    .then(res=>{
        for (const pair of res.headers.entries()){
            console.log(pair[0], ' -> ', pair[1])
            }
        })

```

This code will produce the results:
```
content-type  ->  application/json debugger eval code:1:148
last-modified-version  ->  25 debugger eval code:1:148
link  ->  <https://api.zotero.org/groups/2356093/items?itemType=-attachment&start=25>; rel="next", <https://api.zotero.org/groups/2356093/items?itemType=-attachment&start=25>; rel="last", <https://www.zotero.org/groups/2356093/items>; rel="alternate" debugger eval code:1:148
total-results  ->  32 debugger eval code:1:148
zotero-api-version  ->  3
```

This will alow easy inclusion of links to the next set of search results, as
well as total calculations for the items in the collection.
