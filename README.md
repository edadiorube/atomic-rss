RSS tags for Atomic
---
<details>
<summary>Table of Contents</summary>

* [RSS Elements](https://github.com/ModelRocket/decanter/wiki/Atomic-RSS-Namespace#rss-elements)
* * [\<channel\>](https://github.com/ModelRocket/decanter/wiki/Atomic-RSS-Namespace#channel)
* * [\<atomic:series\>](https://github.com/ModelRocket/decanter/wiki/Atomic-RSS-Namespace#atomicSeries)
* * [\<atomic:subscription\>](https://github.com/ModelRocket/decanter/wiki/Atomic-RSS-Namespace#atomicSubscription)
* * [\<atom:link\>](https://github.com/ModelRocket/decanter/wiki/Atomic-RSS-Namespace#atomLink)
* * [\<atomic:episode\>](https://github.com/ModelRocket/decanter/wiki/Atomic-RSS-Namespace#atomicEpisode)
* [HTTP Query Parameters](https://github.com/ModelRocket/decanter/wiki/Atomic-RSS-Namespace#http-query-parameters)
</details>

Abstract
---

Atomic Publishing provides an aggregated feed that presents multiple podcasts together that provides subscribers with a simpler signup and management experience. The Atomic namespace allows clients to identify and present Atomic Publishing podcasts as either a single stream or as separate items in the user interface yet allowing subscription to a single master feed. 

`<atomic>` elements include `<atomic:series>`, `<atomic:episode>`, and `<atomic:subscription>`. Other RSS elements used in conjunction with atomic include `<channel>`, `<item>`, and `<atom:link>`. The atomic namespace is declared as an xmlns attribute of the `<rss>` tag. For example,

```
<rss xmlns:atomic="http://atomicpublishing.com/rss/1.0/" version="2.0">
```

Within RSS feeds, `<atomic:series>` elements are child elements of `<channel>` and `<atomic:episode>` is a child element of `<item>` as shown in the following example:

```
<rss xmlns:atomic="http://atomicpublishing.com/rss/1.0/" version="2.0"> 
<channel>
  <item>
     <atomic:episode />
  </item>
  <atomic:series>...</atomic:series>
</channel>
```

[RSS Elements](#rss-elements)
---
### [`<channel>`](#channel)

The `<channel>` element contains an entry for every series represented in the feed. For example,

```
<channel>
   ...
   <atomic:series id="57a08a7d-5d7f-4f7f-b726-dcb3de39b610" title="Da Daily Update" expiresAt="2021-04-22T18:16:34.000-07:00">
      ...
   </atomic:series>
   <atomic:series id="58ad5fe1-ef5f-413c-94a5-dec97d62437c" title="Da Dithering" expiresAt="2021-04-22T18:16:34.000-07:00">
      ...
   </atomic:series>
...
</channel>
```

### [`<atomic:series>`](#atomicSeries)

The `<atomic:series>` element has an object id attribute, and it uses child elements `<title>`, `<expiresAt>`, and `<atom:link>`. For example,

```
<atomic:series id="57a08a7d-5d7f-4f7f-b726-dcb3de39b610">
   <title>Stratechery Daily Update</title>
   <atomic:subscription id="1052563">
      <expiresAt>2021-04-25T09:37:22.000-07:00</expiresAt>
   </atomic:subscription>
   <atom:link href="https://rss.atomicpublishing.com/1.0.0/members/1288846/feed?access_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiIiLCJpc3MiOiJjb29wZXIuZGVjYW50ZXIuZm0iLCJpdGEiOiIyMDIwLTA0LTA4VDAyOjAzOjA5Ljc3NVoiLCJqdGkiOiIzNTE4NThkZS1hODQyLTRkM2EtOTEyNC1iY2RkZmFiMmU1OGYiLCJzY29wZSI6ImZlZWQucmVhZCBlcGlzb2RlLnN0cmVhbSIsInN1YiI6IjEyODg4NDYifQ.jSEZW1K56CP6X4GmsIKi-LcNdkTG880AwEYbs0afAl0&series_id=57a08a7d-5d7f-4f7f-b726-dcb3de39b610" rel="related" type="application/rss+xml"/>
</atomic:series>
```

`<atomic:series>` has the following attribute:
|Attribute|Description|
|---|---|
|id|References the full object at `<channel>` level, so each episode can be associated with a series|

`<atomic:series>` uses the following child elements:
|Element|Description|
|---|---|
|`<title>`|the series title|
|`<atomic:subscription>`|Member's subscription|
|`<atom:link>`|url that the podcast can monitor|

### [`<atomic:subscription>`](#atomicSubscription)
`<atomic:subscription>` is present only if a subscription exists; it is not used for free content-only podcasts.
```
   <atomic:subscription id="1052563">
      <expiresAt>2021-04-25T09:37:22.000-07:00</expiresAt>
   </atomic:subscription>
```

`<atomic:subscription` has the following attribute:
|Attribute|Description|
|---|---|
|id|Subscription id|

`<atomic:subscription>` has the following element:

|Element|Description|
|---|---|
|`<expiresAt>`|Expiration date of member's subscription, must be a valid [RFC3339](https://tools.ietf.org/html/rfc3339) date-time string|

### [`<atom:link>`](#atomLink)
Atom is an XML-based document format that describes lists of related information for RSS feeds.

```
<atom:link href="https://atomic.ngrok.io/1.0.0/members/1288846/feed?access_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiIiLCJpc3MiOiJjb29wZXIuZGVjYW50ZXIuZm0iLCJpdGEiOiIyMDIwLTA0LTA4VDAyOjAzOjA5Ljc3NVoiLCJqdGkiOiIzNTE4NThkZS1hODQyLTRkM2EtOTEyNC1iY2RkZmFiMmU1OGYiLCJzY29wZSI6ImZlZWQucmVhZCBlcGlzb2RlLnN0cmVhbSIsInN1YiI6IjEyODg4NDYifQ.jSEZW1K56CP6X4GmsIKi-LcNdkTG880AwEYbs0afAl0&series_id=57a08a7d-5d7f-4f7f-b726-dcb3de39b610" rel="related" type="application/rss+xml"/>
```

`<atom:link>` has the following attributes:

|Attribute|Description|
|---|---|
|href|This attribute is the url that the podcast can monitor for a particular series. The access_token parameter embedded within the url cannot be shared.|
|rel|Set to "related"|
|type|Set to "application/rss+xml"|


### [`<atomic:episode>`](#atomicEpisode)

`<atomic:episode>` is a child element of `<item>`.

```
<item>
   ...
   <atomic:episode id="d2f28489-2bb0-4f96-b3b6-2e6a43b412ba" series="57a08a7d-5d7f-4f7f-b726-dcb3de39b610" type="podcast"/>
</item>
```

`<atomic:episode>` has the following attributes:

|Attribute|Description|
|---|---|
|id|id of episode|
|series|Episode's series id|
|type|Set to "podcast"|

[HTTP Query Parameters](#http-query-parameters)
---
An atomic HTTP query has the following syntax:
```
https://rss.stratechery.com/1.0.0/members/1234/feed?access_token=<your token>&max-length=30
```
The query has the following parameters:
|Parameter|Description|
|---|---|
|access_token|<access_token>, note that the <access_token> cannot be shared.|
|max_length|Maximum number of items to return, regardless of other parameters|
|start_date|Oldest publish date of items to return, must be a valid [RFC3339](https://tools.ietf.org/html/rfc3339) date-time string|
|end_date|Latest publish date of items to return, must be a valid [RFC3339](https://tools.ietf.org/html/rfc3339) date-time string|

Parameters max-length, start-date, and end-date appear after access_token.

