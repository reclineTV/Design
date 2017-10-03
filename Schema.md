# Users

| column | description | type |
|----|---------|--------|
| id | UserId | INT |
| displayName | Display name, like "Luke" | VARCHAR |
| email | Email address (optional) | VARCHAR |
| passhash  | The password hash | VARCHAR |
| created | Timestamp when the user was created at. | DATETIME |
| rank | User rank. Can include 'guest'. | INT |
| ui | Extension ID of the UI this user likes the most | INT |
| theme | Additional theme settings for the UI, JSON | TEXT |
| deleted | True if the favourite was deleted | BOOL |
| active | True if this account has been activated | BOOL |
| dateOfBirth | Users date of birth | DATETIME |
| allowedAgeRating | An override for specific age ratings (and below) this user can view | INT |

# Ranks

The available system ranks.

| column | description | type |
|----|---------|--------|
| id | Rank ID | INT |
| name | The name of this rank | VARCHAR |
| isDefault | Is this rank default/ built in (can't be removed) | BOOL |


admin
normal
guest

# History

| column | description | type |
|----|---------|--------|
| id | UserId | INT |
| userId | The password hash | VARCHAR |
| created | The time this entry was created | DATETIME |
| contentId | ID of the favourited media. | INT |
| contentType | Media = 1, Person = 2, Media Set = 3, Extension = 4. | INT |
| deleted | True if the favourite was deleted | BOOL |

# Content Types

The available content types as a table for convenience.

| column | description | type |
|----|---------|--------|
| id | Content type ID | INT |
| name | Lowercase name. The same as a table name for convenience. | INT |

# Media Sets

Includes albums and series. Nestable.

| column | description | type |
|----|---------|--------|
| id | Set ID | INT |
| parentSet | Optional parent set ID | INT |
| title | The title for the media. | VARCHAR |
| deleted | Was this set deleted? | INT(1) |
| description | Description of the set - e.g. the summary of a series. | TEXT |
| createdBy | ID of the user who created this tag | INT |
| created | Time this tag was created | DATETIME |

# Age Ratings



# Media

Stored media references.

| column | description | type |
|----|---------|--------|
| id | Media ID | INT |
| parentContentId | Parent media/ person/ media set ID. Used for trailers of other media. | INT |
| parentContentType | Media = 1, Person = 2, Media Set = 3, Extension = 4. Used for trailers of other media. | INT |
| type | Media type - video, photo, music | INT |
| title | The title for the media. | VARCHAR |
| age | The age rating of the content. 'U', '18' etc. | VARCHAR |
| ratingGlobal | A global rating, 0-5. | FLOAT |
| duration | Duration in seconds | INT |
| releaseDate | Timestamp of the release/ taken date | DATETIME |
| ratingGlobalUsers | The number of people who have contributed to the global rating | INT |
| rating | Optional local system rating | FLOAT |
| description | Description of the media - e.g. the summary of a movie. HTML. | TEXT |
| created | Timestamp of when this media was created (uploaded) | INT |
| url | Content URL/ file path.  URL can be e.g. youtube://VIDEO_ID or file://. | VARCHAR |
| deleted | True if the favourite was deleted | INT(1) |
| createdBy | ID of the user who created this tag | INT |

# Credits

The list of people in some media - e.g. the artist who made a song, director etc.

| column | description | type |
|----|---------|--------|
| id | Credit ID | INT |
| mediaId | Media ID | INT |
| personId | Person ID | INT |
| role | Role name, e.g. "Director" or "Katniss Everdeen" | VARCHAR |
| description | Role description (if any) | VARCHAR |

# Credited People

People who are credited in media.

| column | description | type |
|----|---------|--------|
| id | Person ID | INT |
| name | Person name | VARCHAR |
| biography | Biography | TEXT |

# Media Tags

Media is tagged by category - romance, comedy, swing, jazz, trailer etc.

| column | description | type |
|----|---------|--------|
| id | Tagged media ID | INT |
| mediaId | Media ID | INT |
| tag | The tag name. Case insensitive, e.g. "Romance" | VARCHAR |
| createdBy | ID of the user who created this tag | INT |
| created | Time this tag was created | DATETIME |

# Favourites

Favourite content

| column | description | type |
|----|---------|--------|
| id | Favourite ID | INT |
| mediaId | Media ID | INT |
| userId | User ID | INT |
| created | Timestamp of when the favourite was created | INT |
| deleted | True if the favourite was deleted | INT(1) |

# Clients (TVs)

System clients

| column | description | type |
|----|---------|--------|
| id | Client ID | INT |
| created | Timestamp the client was created at. | INT |
| name | A friendly name for this client. | VARCHAR |
| deleted | True if the favourite was deleted | INT(1) |

# Client Users

People associated with clients

| column | description | type |
|----|---------|--------|
| id | TV user ID | INT |
| clientId | Client (TV) ID | INT |
| userId | User ID | INT |
| isPrimary | Is this user the primary client user? They'll always be selected by default. | INT(1) |

# Extensions

Extensions are npm packages which are run once at startup and optionally provide a MySQL install script. They can export a search endpoint and e.g. protocol:// handlers.

| column | description | type |
|----|---------|--------|
| id | Extension ID | INT |
| title | Extension Name | VARCHAR |
| description | Extension description | TEXT |
| active | Is this extension active? | INT(1) |
| version | Version number (E.g. 1.2.3) | VARCHAR |
| npmPackage | Package name on npm | VARCHAR |
