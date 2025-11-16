> [!NOTE] from navidrome.org
> ### What exactly is Navidrome?
It is a piece of software that allows you to listen to your own digital music in the same way you would with services like Spotify, Apple Music and others. It also allows you to easily share your music and playlists with your friends and family

After a simple [installation](https://www.navidrome.org/docs/installation/), Navidrome indexes all digital music stored in your hard drive and makes it available through a nice web player and also by using any [Subsonic-API compatible mobile client](https://www.navidrome.org/docs/overview/#apps). Your music becomes searchable and you can create playlists, rate and “favourite” your loved tracks, albums and artists

---

navidrome was the first thing to be set up! it was also the main reason i was doing all this in the first place? i had been wanting to stop using spotify for a while, i was always hating paying a monthly fee to listen to music and i had recently learned about [spotify's CEO owning an AI weapons company](https://www.latimes.com/entertainment-arts/music/story/2025-07-31/spotifys-ceo-owns-an-ai-weapons-company-some-musicians-say-its-time-to-leave), the flooding of the platform with AI slop artists, and running ads for ICE. fuuuck that im out

plus, i had already been getting into physical media with my [[physical music collection/index\|vinyls and cds]], so i was all in for ditching shitty streaming services that prevent you from actually owning the media you pay for.

so, while it took a lot of trial and error, we finally got navidrome up and running. we used the [docker image](https://www.navidrome.org/docs/installation/docker/) in docker compose. i remember having a lot of trouble getting this started. i was super new to linux, and building containers and using the terminal and stuff like this. i honestly still don't even know the term for doing all this is lmfaO previously if you didnt give me an .exe file to run, i would have no idea what to do

but in reality its super simple! first we make the directory and the compose file:

```bash
sudo mkdir navidrome && cd navidrome
sudo nano docker-compose.yml
```

then we can put the following configuration in the compose file:

```yaml
services:
  navidrome:
    image: deluan/navidrome:latest
    user: 1000:1000 # should be owner of volumes
    ports:
      - "4533:4533"
    restart: unless-stopped
    environment:
      # Optional: put your config options customization here. Examples:
      # ND_LOGLEVEL: debug
    volumes:
      - "/path/to/data:/data"
      - "/path/to/your/music/folder:/music:ro"
```

and then you can just start it ??

```bash
docker compose up -d
```

and thats like. literally it. then if you go to http://localhost:4533 , you can see navidrome's login page and get that all started up!

something I remember having trouble with at this point was getting the Last.FM integration to work - for some reason it wasn't liking my API key but we got it working ;; w;;

