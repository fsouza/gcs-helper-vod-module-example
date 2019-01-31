# nginx-vod-module + gcs-helper example

This repository presents an example of
[nginx-vod-module](https://github.com/kaltura/nginx-vod-module) +
[gcs-helper](https://github.com/NYTimes/gcs-helper).

## Running locally

The configuration assumes that video files are under the folder "videos/"
inside the bucket. So in order to run this locally, make sure you have a bucket
with video files inside a "videos/" folder. For example, assuming you want to use a bucket name
"test-gcs-helper" and the [example files provided with
nginx-vod-module-docker](https://github.com/NYTimes/nginx-vod-module-docker/tree/master/examples):

```
[ clone & cd into nginx-vod-module-docker ]
% gsutil mb gs://test-gcs-helper
% gsutil -m cp -r examples/videos gs://test-gcs-helper
```

(If you want to use a different bucket, make sure you update [gcs_helper.env](/gcs_helper.env))

With the files in the correct place, use ``gcloud auth application-default
login`` to get the application credentials in the place expected by the
docker-compose, the run:

```
% docker-compose up
```

After that, HLS and DASH manifest will be available at the following locations:

- HLS: http://localhost:1988/videos/hls/devito/master.m3u8
- DASH: http://localhost:1988/videos/dash/devito/manifest.mpd
- Thumb: http://localhost:1988/videos/t/devito720p/thumb-7000.jpg
