# Python MAL API

[![pypi Version](https://img.shields.io/pypi/v/mal-api.svg?color=informational)](https://pypi.org/project/mal-api/)

An unofficial MyAnimeList API for Python 3.

Currently, the API does not feature any kind of rate limiting. Use the API in moderation and rate limit your queries (0.5 seconds is sufficient to my knowledge). This API uses cached webpage data to increase efficiency and save bandwidth. If you want to refresh your data, you must manually refresh the object.

The API is currently incomplete. More features are to come.

If there are any features that you wish to be supported, please raise an issue. Any feedback is also appreciated.

## Installation and Usage

To install the library: `pip install mal-api`

To import the library: `from mal import *`

## Example

To call the API, you need to create an object.

#### ID Query Example

```python
from mal import Anime

anime = Anime(1) # Cowboy Bebop

print(anime.score) # prints 8.82

anime.reload() # reload object

print(anime.score) # prints 8.81
```

#### Search Query Example

```python
from mal import AnimeSearch

search = AnimeSearch("cowboy bebop") # Search for "cowboy bebop"

print(search.results[0].title) # Get title of first result
```

## Configuration

To configure timeout (default timeout is 5 seconds):

```python
from mal import Anime

from mal import config

config.TIMEOUT = 1  # Import level config

anime = Anime(1, timeout=1)  # Object level config
```

## API Documentation

List of properties/methods currently supported:
```
Anime(mal_id)

Anime.reload()

Anime.mal_id
Anime.title
Anime.title_english
Anime.title_japanese
Anime.title_synonyms
Anime.url
Anime.image_url
Anime.type
Anime.episodes
Anime.status
Anime.aired
Anime.premiered
Anime.broadcast
Anime.producers
Anime.licensors
Anime.studios
Anime.source
Anime.genres
Anime.duration
Anime.rating
Anime.score
Anime.scored_by
Anime.rank
Anime.popularity
Anime.members
Anime.favorites
Anime.synopsis
Anime.background
Anime.related_anime
Anime.opening_themes
Anime.ending_themes
```
```
Manga(mal_id)

Manga.reload()

Manga.mal_id
Manga.title
Manga.title_english
Manga.title_japanese
Manga.title_synonyms
Manga.url
Manga.image_url
Manga.type
Manga.status
Manga.genres
Manga.score
Manga.scored_by
Manga.rank
Manga.popularity
Manga.members
Manga.favorites
Manga.synopsis
Manga.background
Manga.volumes
Manga.chapters
Manga.published
Manga.authors
Manga.related_manga
```
```
AnimeSearch(query)

AnimeSearch.reload()

returns an array of results via .results

AnimeSearchResult.mal_id
AnimeSearchResult.url
AnimeSearchResult.image_url
AnimeSearchResult.title
AnimeSearchResult.synopsis
AnimeSearchResult.type
AnimeSearchResult.episodes
AnimeSearchResult.score
```
```
MangaSearch(query)

MangaSearch.reload()

returns an array of results via .results

MangaSearchResult.mal_id
MangaSearchResult.url
MangaSearchResult.image_url
MangaSearchResult.title
MangaSearchResult.synopsis
MangaSearchResult.type
MangaSearchResult.volumes
MangaSearchResult.score
```
