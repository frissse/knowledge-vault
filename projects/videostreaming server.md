[[IT integratieProject2]]
[[IT GCloud]]


## sources

[[~How To Make Your Own Live Streaming Server]]
[[~Create your own video streaming server with Linux]]
[[~Global HTTP(S) Load Balancing and CDN now support serverless compute]]
[[Automate your VOD transcoding at scale with GCP]] 
[[~transcoding job templates]]
[pub.sub schema used](https://gist.github.com/nazir-kabani/3380de756b892cc414ae7fb348ebf240)

## tools

[[,video.js]]
[[,shaka player]]
[[,ffmpegcore]]

## system design

auto scale app engine?
how to do the transcoding of the videos? backend

pub/sub api
transcoder api

frontend setup

- view voor browsing media: movie en tv-serie apart
- view voor details van de geselecteerde media
- view voor aanpassen media
- view voor login
- view voor bekijken video

api end points - controllers

readMovies
readTvShows
readEpisodeFromTVShow
readMovie
readUser
readGenre

createMovie
createTVShow
createEpisodeFromTvShow

DeleteMovie
DeleteEpisodeFromTvShow
DeleteTvShow