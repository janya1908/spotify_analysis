**1)Retrieve the names of all tracks that have more than 1 billion streams.**
```sql
select * from spotify
where stream>1000000000
```

**2)List all albums along with their respective artists.**
```sql
select 
distinct album,artist
from spotify
order by 1
```

**3)Get the total number of comments for tracks where licensed = TRUE.**
```sql
select 
sum(comments) as total_comments
from spotify
where licensed='true'
```

**4)Find all tracks that belong to the album type single.**
```sql
select * from spotify
where album_type='single'
```

**5)Count the total number of tracks by each artist.**
```sql
select
artist,count(*) as total_songs
from spotify
group by artist
```
**6)Calculate the average danceability of tracks in each album.**
```sql
select album,
avg(danceability) as averageeee
from spotify
group by album
order by 2 desc
```
**7)Find the top 5 tracks with the highest energy values.**
```sql
select track,
max(energy)
from spotify
group by 1
order by 2 desc
limit 5
```
**8)List all tracks along with their views and likes where official_video = TRUE.**
```sql
select track,
sum(views),
sum(likes)
from spotify
where official_video='true'
group by 1
order by 2 desc
```
**9)For each album, calculate the total views of all associated tracks.**
```sql
select album,track,
sum(views)
from spotify
group by 1,2
order by 3 desc
```
**10)Retrieve the track names that have been streamed on Spotify more than YouTube.**
```sql
select*from
(select
track,
coalesce(sum(case when most_played_on='Youtube' then stream end),0) as streamed_on_youtube,
coalesce(sum(case when most_played_on='Spotify'  then stream end),0) as streamed_on_spotify
from spotify
group by 1) as t1
where streamed_on_spotify>streamed_on_youtube
```
**11)Use a WITH clause to calculate the difference between the highest and lowest energy values for tracks in each album.**
```sql
with cte
AS
(select
	album,
	max(energy) as highest_energy,
	min(energy) as lowest_energery
from spotify
group by 1
)
select 
	album,
	highest_energy - lowest_energery as energy_diff
from cte
order by 2 desc
```
