---
layout: post
title: How to classify your music collection by genre. The Ricardo approach.
category: EN
tags: [Coding, R, Raspberry]
---

![Musicbee Screenshot](/images/Posts/2020/2021-06-01_Image1.png){: .center-image }

I have been having a raspberry PI project in mind for way too long time which requires having my music library collection organised. Pretty well organised. I mean when I started it was fairly good organised, by artist name. The title and artist tags were on spot but there was one tag that was a nightmare... The genre tag.

Just so you know the raspberry PI project I have in mind is to have an old radio reconverted into a jukebox, but done in such a way that moving the dial would change to "other radio stations". Those radio stations will automatically choose a song and play it, and the way to select the song will be by a combination of genre and decade. This implies I **need to classify my music into few genres** (20 or 30 at much), each genre must have a decent pool of songs, and finally, every song/band **must have one and only one genre**. Seems easy, well, this task has consumed most of my free time since September 2020, and it isn't over yet!

In this post I will tell you what problems have I encountered, what is the current state of this titanic task and what thing would I have done differently.

## Why classifying by Genre is complicated.

Music genres are like asses. Every single person has one and they are all different. Music bands and artist are not happy to do some nice broad genre. Instead, they will try to have their own style and they usually do it by mixing or combining different styles into their own style. Which will make my life much harder. If a band combines punk with metal. Is it punk? Is it metal? Is it a bird? Is it a plane? Is it a birdplane? In any case, independently of what it is, I do need to assign them one, and so I will.

<!-- more -->

Another common problem is that some artists have a really specific music tag for themselves. This occurs more often than I would like it. (None, I would like to happen ZERO times!) Do I really want to classify Cartoons in the [tecnobilly](https://www.last.fm/tag/technobilly){:target="_blank"} genre? No, I don't, why anybody would like that, you might as well click on the artist instead. So very specific bands will be assigned a broader genre, and if not possible, they will be exiled into the wretched genre of "other", and more likely they won't be played again!

Genre is also attached to what type of music does one hears, and their own music collection. If someone is really passionate about electronic music, you might want to have several tags or genres for the different styles (House, Ambient, Disco, Electro Swing) whilst if you have just a few songs you might want to classify them under Electronic/EDM, or even ignore the genre and assign it to another genre.

So the first step to start is, **you need to come up with a list of genres**, and this list must be sensible with what you listen to. Because I had no idea how to start I used someone else already made list: the [ID3v1 list of genres](https://en.wikipedia.org/wiki/List_of_ID3v1_Genres). This provided me with a nice 80 tags to start with. Few tweaks here and there like, removing the *Top 40* , or *Gospel* tag, and add some more like EDM to group modern electronica (Techno, House, etc...) and separate it from classic electronic music (Tubular Bells, Michael Jean Jarre) and we are fine to go, or so I thought...

The thing is when one start with the actual classifying process you tend to create a few genres that will contain very few songs. For instance in my case: **New Age**, **Psychedelic**, and **Vocal** contain less than 20 songs combined. On the other hand, other genres will accumulate most of the song in my collection, **Classic Rock** has 710 songs, **Pop** has 1015 songs, whilst the whole library contains 3982 songs.

![Library Statistic](/images/Posts/2020/2021-06-01_Image2.png){: .center-image }

I am currently reiterating all the process and trying to divide **Pop** into other subgenres like **New Wave** (already done), **electropop** (currently working on this).

## Software to auto-sort by Genre

Several tools will help you to organise your music collection. The most famous (and free) is the [Music Brainz Picard](https://picard.musicbrainz.org/){:target="_blank"}. This software will scan your music collection, assign them an ID using some kind of fancy Hash for music. Compare with their own community giant database collection and retrieve the information.

The system does a very good job, but it will have some terrible errors. So it is not a good idea to use it unattended and believe everything it says unless your music collection has zero to no organisation beforehand. Keeping an eye on what it does is as tedious as doing it by yourself. So I discard this system to organise by genre. But I did use it to organise the year. It did a subpar job, but as the year tag of my collection was already empty, I accepted it as it was.

There are plenty of privative (and quite expensive) [alternatives](https://alternativeto.net/software/musicbrainz-picard/?p=2){:target="_blank"}, TuneUp, Jaikoz, Metadatics... I tried the trial versions of the alternatives with a "selected sample of songs". Their outcome was... not satisfactory either. So manual sorting was the only other option.

## Assigning artist/songs to genre

I decided to assign every artist to a genre. And only if certain artist have two very different genres in their career (Dover for example: [rock](https://www.last.fm/music/Dover/_/Devil+Came+to+Me){:target="_blank"} and [electropop](https://www.last.fm/music/Dover/_/Let+Me+Out)){:target="_blank"} would be deal in a song basis.

In a nod to Plato's [theory of forms](https://en.wikipedia.org/wiki/Theory_of_forms){:target="_blank"}, I decided to give to every genre a master song. The master song will act as an "Idea" or "Form" of the genre. Like the only true representation of that genre. Any other song will be classified into the same genre _if they could be listened to in the same "Radio Station"_ than the master song. If not, they would need to go to another genre or be exiled into the "other" genre. Just for your amusement below is my list of "Form songs". 

| Genre            | Songs |Info| Canción                    |
|:----------------:|:-----:|:--:|:--------------------------:|
| alternative rock  | 393   |    | [Muse – Resistance](https://www.last.fm/music/Muse/_/Resistance){:target="_blank"}                                              |
| ambient           | 19    |    | [Mauro Picotto – Adiemus](https://www.last.fm/music/Mauro+Picotto/_/Adiemus){:target="_blank"}                                  |
| blues             | 11    |    | [Leonard Cohen – Suzanne](https://www.last.fm/music/Leonard+Cohen/_/Suzanne){:target="_blank"}                                  |
| classic rock      | 710   |    | [Dire Straits – Sultans of Swing](https://www.last.fm/music/Dire+Straits/_/Sultans+of+Swing){:target="_blank"}                  |
| classical         | 1     | A  | [Ludovico Einaudi – Nuvole Bianche](https://www.last.fm/music/Ludovico+Einaudi/_/Nuvole+Bianche){:target="_blank"}              |
| country           | 36    |    | [Toby Keith – God Love Her](https://www.last.fm/music/Toby+Keith/_/God+Love+Her){:target="_blank"}                              |
| disco             | 67    |    | [Earth, Wind & Fire – Boogie Wonderland](https://www.last.fm/music/Earth,+Wind+&+Fire/_/Boogie+Wonderland){:target="_blank"}    |
| edm               | 33    |    | [Avicii – Hey Brother](https://www.last.fm/music/Avicii/_/Hey+Brother){:target="_blank"}                                        |
| electronic        | 84    |    | [Jean Michel Jarre](https://www.last.fm/music/Jean+Michel+Jarre/_/Oxygene,+Pt.+4){:target="_blank"}                             |
| electropop        | 8     | B  | [Owl City – Fireflies](https://www.last.fm/music/Owl+City/_/Fireflies){:target="_blank"}                                        |
| eurodance         | 27    |    | [Eiffel 65 – Blue](https://www.last.fm/music/Eiffel+65/_/Blue+(Da+Ba+Dee)){:target="_blank"}                                    |
| folk              | 28    |    | [Simon & Garfunkel – The sound of silence](https://www.last.fm/music/Simon+&+Garfunkel/_/The+Sound+of+Silence){:target="_blank"}|
| freak metal       | 82    |    | [El Reno Renardo – El Bogavante](https://www.last.fm/music/El+Reno+Renardo/_/El+Bogavante){:target="_blank"}                    |
| gothic            | 4     | A  | [Evanescence – Lithium](https://www.last.fm/music/Evanescence/_/Lithium){:target="_blank"}                                      |
| grunge            | 18    |    | [The Smashing Pumpkins – Bullet With Butterfly Wings](https://www.last.fm/music/The+Smashing+Pumpkins/_/Bullet+With+Butterfly+Wings+-+remastered+2012){:target="_blank"}       |
| hard rock         | 107   |    | [Scorpions - She's Knocking At My Door](https://www.youtube.com/watch?v=STJyN4RCLXs){:target="_blank"}                          |
| hip-hop           | 50    | C  | [Eminem – Lose Yourself](https://www.last.fm/music/Eminem/_/Lose+Yourself){:target="_blank"}                                    |
| jazz              | 61    |    | [Louis Armstrong – What a Wonderful World](https://www.last.fm/music/Louis+Armstrong/_/What+a+Wonderful+World){:target="_blank"}|
| latin             | 14    |    | [Miami Sound Machine – Conga](https://www.last.fm/music/Miami+Sound+Machine/_/Conga){:target="_blank"}                          |
| lo-fi             | 1     | D  | [Grizzly Bear – Two Weeks](https://www.last.fm/music/Grizzly+Bear/_/Two+Weeks){:target="_blank"}                                |
| metal             | 36    |    | [Stratovarius – 4000 Rainy Nights](https://www.last.fm/music/Stratovarius/_/4000+Rainy+Nights+(Remastered+2016)){:target="_blank"}|
| new age           | 2     | D  | [Sally Oldfield – Mirrors](https://www.last.fm/music/Sally+Oldfield/_/Mirrors){:target="_blank"}                                |
| new wave          | 234   |    | [Alphaville – Forever Young](https://www.last.fm/music/Alphaville/_/Forever+Young){:target="_blank"}                            |
| oldies            | 584   |    | [The Foundations – Build Me Up Buttercup](https://www.last.fm/music/The+Foundations/_/Build+Me+up+Buttercup){:target="_blank"}  |
| other             | 39    |    | Were exiled song come to die                                                                                  |
| pop               | 1015  | E  | [Coldplay – The Hardest Part](https://www.last.fm/music/Coldplay/_/The+Hardest+Part){:target="_blank"}                          |
| psychedelic       | 2     | D  | [? and The Mysterians – 96 Tears](https://www.last.fm/music/%3F+and+the+Mysterians/_/96+Tears){:target="_blank"}                |
| punk              | 92    |    | [The Offspring – Pretty Fly](https://www.last.fm/music/The+Offspring/_/Pretty+Fly+(For+a+White+Guy)){:target="_blank"}          |
| reggae            | 25    |    | [Eddy Grant – Gimme Hope Jo’anna](https://www.last.fm/music/Eddy+Grant/_/Gimme+Hope+Jo%27anna){:target="_blank"}                |
| rock              | 104   |    | [Men at Work – Down Under](https://www.last.fm/music/Men+at+Work/_/Down+Under){:target="_blank"}                                |
| rockabilly        | 5     |    | [The Baseballs – Umbrella](https://www.last.fm/music/The+Baseballs/_/Umbrella){:target="_blank"}                                |
| ska               | 5     | D  | [Streetlight Manifesto – A Moment of Silence](https://www.last.fm/music/Streetlight+Manifesto/_/A+Moment+Of+Silence){:target="_blank"}        |
| soul              | 70    |    | [Roberta Flack – Killing Me Softly with his song](https://www.last.fm/music/Roberta+Flack/_/Killing+Me+Softly+With+His+Song){:target="_blank"}|
| soundtrack        | 14    |    | [John Travolta – Greased Lightnin’](https://www.last.fm/music/John+Travolta/_/Greased+Lightnin%27){:target="_blank"}                          |
| vocal             | 1     | D  | [The Blanks – Hey ya!](https://www.youtube.com/watch?v=8K0EAc3abq8){:target="_blank"}                                           |

A. There is another music collection that will eventually join this one and will enlarge this genre.
B. Electropop has been recently created to reduce the size of the pop genre.
C. Includes also Rap to create a larger song pool.
D. This genre will be removed due to having a small pool of songs.
E. Pop has been quite overused genre, and a second revision of those must be done to reclass them.

## Getting some extra help before manual sorting

First of all, is getting all the information from our music collection in a format we can import into R. [Tagscanner](https://www.xdlab.ru/en/){:target="_blank"} is our man. Scan your library, and in the export tab, save it as an "Excel friendly" CSV file. Don't forget to check the UTF-8 with DOM option. Mind that from this moment until you finish, you must not modify your library by adding, removing or editing any file here.

The next step is to get a [last.fm API](https://www.last.fm/api){:target="_blank"} so we can call it from our R code. Sign in for an API request and get your API key, your API key is a hexadecimal number that should look similar to this one "0123456789abcdef0123456789abcdef". 

The next step, get R and Rstudio ready and install the urltools, jsonlite, memoise and curl packages. We will be creating some functions that will help us to retrieve information from last.fm database.

	library(urltools)
	library(jsonlite)
	
	# Add your Last.fm API Here
	lastFM_API = "0123456789abcdef0123456789abcdef"
	
	# This function returns the JSON URL for certain Artist
	build_artist_info <- function(artist,  api_key= lastFM_API, base = "http://ws.audioscrobbler.com/2.0/"){
	base <- param_set(base, "method", "artist.getInfo")
	base <- param_set(base, "artist", URLencode(artist))
	base <- param_set(base, "api_key", api_key)
	base <- param_set(base, "format", "json")
	return(base)
	}
	

The function: *build_artist_info(artist = "Aqua")*, does the same, but in this case, the URL will point to the artist JSON information, which contains information such as similar artist, their wiki entry, genre tags, etc...

We now need to read this JSON file. This can be done with the function fromJSON().

	fromJSON(build_artist_info(artist = "Aqua"))

This function will provide with a list of lists that contain the JSON information. Accessing to the top 5 last.fm genre is as easy as navigating through the data to:

	fromJSON(build_artist_info(artist = "Aqua"))$artist$tags$tag$name

Now we are ready to:

Mind that I am reading the tracklist without a header because Tagscanner doesn't give one. That I am using the defaults values of Tagscanner. That my separator is ";" because I am in a Spanish computer, and I am forcing reading every column as a character and the file encoding. 

	# Read the csv with the library information
	tracklist = read.table(r"(B:\Documents\R\RMusicOrganiser\tracklist_MBID.csv)", header = FALSE, sep = ";", fileEncoding = "UTF-8-BOM", colClasses = rep("character",14))
	
	# Get a list of Artists
	UniqueArtistList = unique(tracklist$V2)
	
	# For each artist, provide me with the 5 top genre tags
	ArtistGenresList = sapply( UniqueArtistList, function(x){fromJSON(build_artist_info(x))$artist$tags$tag$name})

Depending on the size of your artist list, this command can take a while to run. You will end up with a list of artist, which contains a list of 5 tags, or an empty list if they couldn't find the artist. Now you could write a fancy code to prioritise some tags over others (Dance > Pop, Classic Rock > Rock) to help you auto-tagging, I tried this initially but in the end is not better than using Music Brainz. Chances are that you end up having to review all information so I decided to export all info into a spreadsheet instead.

This piece of code is to get a data frame with the artist, the 5 genres and a score for each one (starting at 0).

	# Create Empty data.frame
	df3 = data.frame()
	
	# Function to expand data
	expand_genre_todf <- function(x){
		y = unlist(x)
		if (length(y) == 5) {
			res = data.frame(Artist = names(x),
					genre1 = y[1],F1 = 0,
					genre2 = y[2],F2 = 0,
					genre3 = y[3],F3 = 0,
					genre4 = y[4],F4 = 0,
					genre5 = y[5],F5 = 0,
					row.names = NULL)
		} else {
			res = data.frame(Artist = names(x),
					genre1 = NA,F1 = 0,
					genre2 = NA,F2 = 0,
					genre3 = NA,F3 = 0,
					genre4 = NA,F4 = 0,
					genre5 = NA,F5 = 0,
					row.names = NULL)
		}
		return(res)
	}
	
	# Build dataframe
	for (i in 1:length(ArtistGenresList)) {
		df3 = rbind(df3, expand_genre_todf(ArtistGenresList[i]))
	}

Now if you view df3, you can see I have left a numeric value of 0 next to every tag. This is the score I will give to each tag to help me when selecting. I decided to go very simple, the score will be 0 if is not in my master genre list and 1 if it is. I will make this value 1 if the genre next to it is in our master genre list. I have created a CSV with our genre master list.

	# Read our list of genres
	genrelist = read.table(r"(B:\Documents\R\RMusicOrganiser\_ss\GenreList.csv)", header = FALSE, sep = ",", fileEncoding = "UTF-8")$V1

![Musicbee Screenshot](/images/Posts/2020/2021-06-01_Image4.png){: .center-image }

And I go one by one checking if each of the 5 genres is in the master list. At first, I just did a simple string comparison. But it didn't work as expected. Last.fm tags are not standardised at all and hip-hop might appears as Hip-Hop, HipHop, hip hop, or any other similar value. Simple string comparison with (my genre) "hip-hop" would give me a positive false. Instead, I am converting everything into capital letters, and using a coefficient between the function adist and the number of characters to check if the tags are similar enough. The value of 0.2 was found after trial and error, and consistently produced good results with almost no false positives.

	# Add filtering
	for (i in c(2,4,6,8,10)){
	  for (j in 1:nrow(df3)){
		xg = toupper(df3[j,i])
		if (!is.na(xg)){
		  if (any(adist(xg,toupper(genrelist))/nchar(xg) < 0.2)) {df3[j,i+1]=1}
		}
	  }
	}

And we can end up by writing this file into a CSV that we can open with your favourite calc sheet programs. 

	write.table(df3, file = r"(B:\Documentos\GitHub\RMusicOrganiser\Artist_Genre.csv)",
				sep = ",",
				row.names = FALSE)


