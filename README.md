# Khlyrics

Khmer song lyrics database. Use this repo as a data source for your app.

## Data Structure

- `songs.json` - Index of all songs with metadata
- `md/` - Lyrics in Markdown format

## API Usage

### Fetch Song List

```javascript
const res = await fetch('https://raw.githubusercontent.com/im4tta/khlyrics/main/songs.json');
const songs = await res.json();
```

### Fetch Lyrics

```javascript
const res = await fetch(`https://raw.githubusercontent.com/im4tta/khlyrics/main/md/${encodeURIComponent(song.file)}`);
const lyrics = await res.text();
```

### Search by Title

```javascript
const results = songs.filter(s =>
  s.title.includes(query) || s.titleEn.toLowerCase().includes(query.toLowerCase())
);
```

### Search by Location

```javascript
const results = songs.filter(s => s.location.includes(query));
```

## songs.json Schema

| Field | Type | Description |
|-------|------|-------------|
| `title` | string | Song title in Khmer |
| `titleEn` | string | English/romanized title |
| `artist` | string | Singer name |
| `composer` | string | Composer name |
| `location` | string | Location mentioned in song |
| `year` | string | Year released |
| `file` | string | Filename in `md/` directory |
