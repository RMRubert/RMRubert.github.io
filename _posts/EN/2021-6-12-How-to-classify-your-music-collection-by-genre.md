---
layout: post
title: How to classify your music collection by genre. The Ricardo approach.
category: EN
tags: [Music, Coding, R]
---

![Musicbee Screenshot](/images/Posts/2021/2021-06-12_Image1.png){: .center-image }

This post is about how did I organise my music library by genre. I have not done it for the sake of organisation (well, maybe a little), but because it is part of a bigger project. This (bigger) project is to have an old radio reconverted with a Raspberry PI in such a way that turning the dial will let the user choose different radio stations. Each radio station will play a set of songs, and it will be defined by a combination of genre and decade.

Because the organisation serves a purpose to the project, the classification had to be done with a set of rules (aka **The Radio Rules!**):
1. Few genres. Between 15 and 25.
2. Each genre should have a decent pool of songs. I do not want a radio playing 6 songs time after time, I already have KISS FM Spain for that.
3. Each song must be categorised using only one genre.

Easy! Well, this task has consumed most of my free time since September 2020, and it isn't over yet!

But Ricardo, shall I have any learning expectations from this post? Well, mostly no. This is a small resume of what you will find in the post:
1. An explanation on why classifying by genre is pointless and most people have already given up.
2. The currently existing software to automatise this task.
3. Me ignoring every piece of software and instead, using Plato's theory to classify my library in a list of genres.
4. How to get a CSV file with information about your library collection.
5. How to use R and last.fm API to retrieve information about an artist genre (this is the only section in which, potentially, you will actually learn something)

<!-- more -->

## Why classifying by Genre is complicated.

![Library Statistic](/images/Posts/2021/2021-06-12_Image2.png){: .center-image }

When I started this task I used my favourite search engine to see how can it be done. I ended up in some music forums and a lot of answers were that people gave up on classifying by genre. Why? Because genres are subjective. If I ask you who is the original artist of "Girls just wanna have fun", there is only one right answer: [Robert Hazard.](https://www.last.fm/music/Robert+Hazard/_/Girls+Just+Wanna+Have+Fun){:target="_blank"} You don't get a simple answer when doing the same question about the genre. If you are a fan of Electronic music you might want to tag all the different styles (House, Ambient, Disco, Dub, Electro Swing...) whilst for another person (me!) all those styles might go under the tag EDM (In my case, the EDM tag is to group modern electronica like Techno, House, etc., and differentiate them from classic electronic music like Tubular Bells or Michael Jean Jarre).

Another problem is the gradualness of genres. Musicians have an inherent problem with making music that can be categorised into a nice simple genre. Those little bastards will try to have their own "style" and do you know how they do that? Yes, exactly, they got two genres and mix them (and not even 50%/50%). If a band now combines punk with metal. Is it punk? Is it metal? Is it a bird? Is it a plane? Is it a birdplane? This could not be a problem, but it collides with the set rule of only one genre per song.

This leads to the following quandary, uniqueness. Some artists have managed to create a genre so specific that no other band in the world plays. This occurs more often than I would like it. (Which is none, I would like to happen *"none"* times!) Do I really want to classify Cartoons in the [tecnobilly](https://www.last.fm/tag/technobilly){:target="_blank"} tag? No, I don't, why anybody would like that? Plus it collides with each genre should have a decent pool of songs rule. A decision was taken, if some musician managed to invent a genre so specific that couldn't be assigned to a broader genre(a.k.a. piss me off), then, their songs will be exiled into the wretched genre of "other", and more likely they won't be played again!

Resuming, classifying genres ain't easy because of subjectivity, gradualness and uniqueness. So how did I solve this? Come up with a predefined list of genres. The list must have enough genres to successfully divide the music collection into sensible categories and adapt to my own criteria and library.

So the first step to start is, **you need to come up with a list of genres**. My starting point was the [ID3v1 list of genres](https://en.wikipedia.org/wiki/List_of_ID3v1_Genres){:target="_blank"}. The list contains a nice 80 tags to start with. Remove some tags (Top 40, Gospel) and add some other tags (EDM). Whatever list you come with here, you will change it later. This process is mostly iterative.

You don't know how many songs will you have in a genre until you start. This translates into ending up with some genres with very few songs, and others including one-third of the music collection. In my case: **New Age**, **Psychedelic**, and **Vocal** contain less than 20 songs combined. Whilst, **Classic Rock** has 710 songs, and the almighty **Pop** has 1015 songs. Classic Rock and Pop are 43% of my library.

I am currently reiterating all the process and trying to divide **Pop** into other subgenres like **New Wave** (already done) or **electropop** (currently working on this).

## Software to auto-sort by Genre

![The garbage man](/images/Posts/2021/2021-06-12_Image3.jpeg){:.center-image }

But can't someone else just do it? Technically yes, but it will be a subpar job. The subjectivity, graduality and uniqueness will come to and screw up with your plans of letting a tool work for you. But if you do not trust me you can go and test them by yourself. Do what I did, create a 50 songs sample (Trial periods are limited to a certain amount of songs) and check if you are happy with their results.

I will recommend you to start with the free [Music Brainz Picard](https://picard.musicbrainz.org/){:target="_blank"}. This software will scan your music collection, assign them a "magic music hash id". And compare with their own community giant database collection to retrieve the information.

But Ricardo, what if I think that you are a case of long pockets and short arms? What if one could spend some of their hard-earned sterling pounds and exchange them for goods and services. Services like finding a tool that just does it? Well, good news is that there are plenty of paid [alternatives](https://alternativeto.net/software/musicbrainz-picard/?p=2){:target="_blank"}.

Do not get me wrong, the tools work quite alright, almost like magic. But there are two problems: 
1. They cannot work unattended, and if I need to revise everything they suggest me to do, the process is as slow as doing it by myself. 
2. The way they work collides with my _three radio rules_.

## Getting philosophical about music classification

I decided to assign every artist to a genre (as opposed to classify each song). And only if a certain artist have two very different genres in their career (Dover for example: [rock](https://www.last.fm/music/Dover/_/Devil+Came+to+Me){:target="_blank"} and [electropop](https://www.last.fm/music/Dover/_/Let+Me+Out){:target="_blank"} would be dealt in a song to song basis.

![Plato listening to some form songs](/images/Posts/2021/2021-06-12_Image5.png){: .center-image }

But then I started to get philosophical. How can I determine what is Rock from what it isn't? Is it Aerosmith rocker than Dire Straits? But why make myself such a question when great thinkers have already discussed plenty of theories? So in a nod to Plato's [theory of forms](https://en.wikipedia.org/wiki/Theory_of_forms){:target="_blank"}, I decided to give to every genre a master song. The master song will act as an "Idea" or "Form" of the genre. Like it is the only true representation of that genre.

When I will have doubts about an artist being one or another genre, I will make myself the question, _if I was the Radio Station DJ of the genre, will I play it next to the master song?_ If they couldn't be played next to any master song, they would be exiled into the "other" tag.

Are you curious to know my list of "Form songs". There you have.

| Genre            | Songs |Info| Canción                    |
|:----------------:|:-----:|:--:|:--------------------------:|
| alternative rock  | 393   |    | [Muse – Resistance](https://www.last.fm/music/Muse/_/Resistance){:target="_blank"}                                              |
| ambient           | 19    |    | [Mauro Picotto – Adiemus](https://www.last.fm/music/Mauro+Picotto/_/Adiemus){:target="_blank"}                                  |
| blues             | 11    |    | [Leonard Cohen – Suzanne](https://www.last.fm/music/Leonard+Cohen/_/Suzanne){:target="_blank"}                                  |
| classic rock      | 710   |    | [Dire Straits – Sultans of Swing](https://www.last.fm/music/Dire+Straits/_/Sultans+of+Swing){:target="_blank"}                  |
| classical         | 1     | 1  | [Ludovico Einaudi – Nuvole Bianche](https://www.last.fm/music/Ludovico+Einaudi/_/Nuvole+Bianche){:target="_blank"}              |
| country           | 36    |    | [Toby Keith – God Love Her](https://www.last.fm/music/Toby+Keith/_/God+Love+Her){:target="_blank"}                              |
| disco             | 67    |    | [Earth, Wind & Fire – Boogie Wonderland](https://www.last.fm/music/Earth,+Wind+&+Fire/_/Boogie+Wonderland){:target="_blank"}    |
| edm               | 33    |    | [Avicii – Hey Brother](https://www.last.fm/music/Avicii/_/Hey+Brother){:target="_blank"}                                        |
| electronic        | 84    |    | [Jean Michel Jarre – Oxygene, Pt 4](https://www.last.fm/music/Jean+Michel+Jarre/_/Oxygene,+Pt.+4){:target="_blank"}                             |
| electropop        | 8     | 2  | [Owl City – Fireflies](https://www.last.fm/music/Owl+City/_/Fireflies){:target="_blank"}                                        |
| eurodance         | 27    |    | [Eiffel 65 – Blue](https://www.last.fm/music/Eiffel+65/_/Blue+(Da+Ba+Dee)){:target="_blank"}                                    |
| folk              | 28    |    | [Simon & Garfunkel – The sound of silence](https://www.last.fm/music/Simon+&+Garfunkel/_/The+Sound+of+Silence){:target="_blank"}|
| freak metal       | 82    |    | [El Reno Renardo – El Bogavante](https://www.last.fm/music/El+Reno+Renardo/_/El+Bogavante){:target="_blank"}                    |
| gothic            | 4     | 1  | [Evanescence – Lithium](https://www.last.fm/music/Evanescence/_/Lithium){:target="_blank"}                                      |
| grunge            | 18    |    | [The Smashing Pumpkins – Bullet With Butterfly Wings](https://www.last.fm/music/The+Smashing+Pumpkins/_/Bullet+With+Butterfly+Wings+-+remastered+2012){:target="_blank"}       |
| hard rock         | 107   |    | [Scorpions - She's Knocking At My Door](https://www.youtube.com/watch?v=STJyN4RCLXs){:target="_blank"}                          |
| hip-hop           | 50    | 3  | [Eminem – Lose Yourself](https://www.last.fm/music/Eminem/_/Lose+Yourself){:target="_blank"}                                    |
| jazz              | 61    |    | [Louis Armstrong – What a Wonderful World](https://www.last.fm/music/Louis+Armstrong/_/What+a+Wonderful+World){:target="_blank"}|
| latin             | 14    |    | [Miami Sound Machine – Conga](https://www.last.fm/music/Miami+Sound+Machine/_/Conga){:target="_blank"}                          |
| lo-fi             | 1     | 4  | [Grizzly Bear – Two Weeks](https://www.last.fm/music/Grizzly+Bear/_/Two+Weeks){:target="_blank"}                                |
| metal             | 36    |    | [Stratovarius – 4000 Rainy Nights](https://www.last.fm/music/Stratovarius/_/4000+Rainy+Nights+(Remastered+2016)){:target="_blank"}|
| new age           | 2     | 4  | [Sally Oldfield – Mirrors](https://www.last.fm/music/Sally+Oldfield/_/Mirrors){:target="_blank"}                                |
| new wave          | 234   |    | [Alphaville – Forever Young](https://www.last.fm/music/Alphaville/_/Forever+Young){:target="_blank"}                            |
| oldies            | 584   |    | [The Foundations – Build Me Up Buttercup](https://www.last.fm/music/The+Foundations/_/Build+Me+up+Buttercup){:target="_blank"}  |
| other             | 39    |    | Where exiled song come to die                                                                                  |
| pop               | 1015  | 5  | [Coldplay – The Hardest Part](https://www.last.fm/music/Coldplay/_/The+Hardest+Part){:target="_blank"}                          |
| psychedelic       | 2     | 4  | [? and The Mysterians – 96 Tears](https://www.last.fm/music/%3F+and+the+Mysterians/_/96+Tears){:target="_blank"}                |
| punk              | 92    |    | [The Offspring – Pretty Fly](https://www.last.fm/music/The+Offspring/_/Pretty+Fly+(For+a+White+Guy)){:target="_blank"}          |
| reggae            | 25    |    | [Eddy Grant – Gimme Hope Jo’anna](https://www.last.fm/music/Eddy+Grant/_/Gimme+Hope+Jo%27anna){:target="_blank"}                |
| rock              | 104   |    | [Men at Work – Down Under](https://www.last.fm/music/Men+at+Work/_/Down+Under){:target="_blank"}                                |
| rockabilly        | 5     |    | [The Baseballs – Umbrella](https://www.last.fm/music/The+Baseballs/_/Umbrella){:target="_blank"}                                |
| ska               | 5     | 4  | [Streetlight Manifesto – A Moment of Silence](https://www.last.fm/music/Streetlight+Manifesto/_/A+Moment+Of+Silence){:target="_blank"}        |
| soul              | 70    |    | [Roberta Flack – Killing Me Softly with his song](https://www.last.fm/music/Roberta+Flack/_/Killing+Me+Softly+With+His+Song){:target="_blank"}|
| soundtrack        | 14    |    | [John Travolta – Greased Lightnin’](https://www.last.fm/music/John+Travolta/_/Greased+Lightnin%27){:target="_blank"}                          |
| vocal             | 1     | 4  | [The Blanks – Hey ya!](https://www.youtube.com/watch?v=8K0EAc3abq8){:target="_blank"}                                           |

1. There is another music collection that will eventually join this one and will enlarge this genre.
2. Electropop has been recently created to reduce the size of the pop genre.
3. Includes also Rap to create a larger song pool.
4. This genre will be removed due to having a small pool of songs.
5. Pop has been quite an overused genre. I am (re-)reviewing it to reduce its size.

## Less philosophy and more coding!

![Time to code!](/images/Posts/2021/2021-06-12_Image7.png){: .center-image }

I have written this post to teach philosophy and code in R... and I'm all out of theories.

We need to pass library info to R, so we need a CSV file with information about our library. [Tagscanner](https://www.xdlab.ru/en/){:target="_blank"} is our man. Scan your library, and in the export tab, save it as an "Excel friendly" CSV file. Don't forget to check the UTF-8 with DOM option. Mind that from this moment until you finish, you **must not modify your library by adding, removing or editing any file here**. 

Then we need a database to get information from. Get a [last.fm API](https://www.last.fm/api){:target="_blank"} so we can access their database and load it into our R code. Sign in for an API request and get your API key, your API key is a hexadecimal number that should look similar to this one "0123456789abcdef0123456789abcdef", and gives you permission to use their database. 

If you don't have R and Rstudio ready go download and install them. You will also need the urltools and jsonlite libraries. We will be creating some functions that will help us to retrieve information from last.fm database.

	library(urltools)
	library(jsonlite)
	
	# Add your Last.fm API Here
	lastFM_API = "0123456789abcdef0123456789abcdef"
	
	# This function returns the JSON URL for certain Artist
	build_artist_info <- function(artist,
			api_key= lastFM_API,
			base = "http://ws.audioscrobbler.com/2.0/"){
		base <- param_set(base, "method", "artist.getInfo")
		base <- param_set(base, "artist", URLencode(artist))
		base <- param_set(base, "api_key", api_key)
		base <- param_set(base, "format", "json")
		return(base)
	}
	

The function: *build_artist_info(artist = "Aqua")* generates a URL pointing to the Artist requested (Aqua in this example) JSON file with information about them. If the artist doesn't exist it won't return anything. If you copy this URL into Firefox, you can take a look at the JSON file.

But we don't need to load the JSON in firefox, we need the data to be in R. The way to do this is using the function fromJSON().

	fromJSON(build_artist_info(artist = "Aqua"))

This function will read the JSON, and convert it to an R format (list of lists). Don't hesitate to save this into a dummy variable and check the info in the environment panel of Rstudio, it shouldn't differ from what you saw on Firefox. To access the top 5 last.fm genre is as easy as navigating through the data to:

	fromJSON(build_artist_info(artist = "Aqua"))$artist$tags$tag$name

![Rstudio showing my real last.fm API](/images/Posts/2021/2021-06-12_Image6.png){: .center-image }

With our new superb functions, we are ready to import the tracklist from step 1 into R and start getting genres! You will have to read the tracklist without a header because Tagscanner doesn't give one. Mind that in my example code snip shown below has been set in this way because I am using the defaults values of Tagscanner, that my separator is ";" because I am in a Spanish computer, and I am forcing reading every column as a character and forcing the file encoding. 

	# Read the csv with the library information
	tracklist = read.table(r"(B:\Doc...\tracklist.csv)",
		header = FALSE,
		sep = ";",
		fileEncoding = "UTF-8-BOM",
		colClasses = rep("character",14))
	
	# Get a list of Artists
	UniqueArtistList = unique(tracklist$V2)
	
	# For each artist, provide me with the 5 top genre tags
	ArtistGenresList = sapply( UniqueArtistList, function(x){fromJSON(build_artist_info(x))$artist$tags$tag$name})

Depending on the size of your artist list, this command can take a while to run, so it wouldn't hurt trying in a subset of artists first. You will end up with a list of artist, which contains a list of 5 tags, or an empty list if they couldn't find the artist (likely you wrote the artist name incorrectly). 

At this point, I decided to code some really fancy scripts to auto-tag everything based on few rules (like checking decade and genre with my list of genres, and prioritising one tag over others tag, condense them into a single tag, etc...). Remember what I said about the tools that help you doing the classification? Yes, they suck! Well, turns out that my script was doing a subpar job too. Chances are that you end up having to review all information so I decided to export all info into a spreadsheet instead, and go fully manual from here.

This piece of code is to get a data frame with the artist, the 5 genres and a score for each one (starting at 0). The score should help you decide which genre is more suitable, more details below.

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

The scoring system can be as complicated as you want, I decided to keep it simple (Lies!, I started doing an extremely complex scoring system that turned out to be rubbish, then went to the simple system). The score will be 0 if the last.fm genre is not in my master genre list and 1 if it is. The code shown below is a little bit more complicated than just comparing two string, I called it "the smarter string comparison". Don't judge me, I need to keep coming with those catchy names to keep you reading 

Why the smarter string comparison? A simple string comparison between "hip-hop" and "Hip Hop" would give me a false, which I don't want. To solve this, I am converting everything into capital letters, and generating a coefficient between them with the function adist and the number of characters to check if the tags are similar enough. The value of 0.2 was found after trial and error, and consistently produced good results with almost no false positives. If my Fortran90 teacher who (tried) taught me to avoid using magic numbers reads this post, I am really sorry Don Requena, it will not happen again.

	# Read our list of genres
	genrelist = read.table(r"(B:\Documents\R\RMusicOrganiser\_ss\GenreList.csv)", header = FALSE, sep = ",", fileEncoding = "UTF-8")$V1
	# Add filtering
	for (i in c(2,4,6,8,10)){
	  for (j in 1:nrow(df3)){
		xg = toupper(df3[j,i])
		if (!is.na(xg)){
		  if (any(adist(xg,toupper(genrelist))/nchar(xg) < 0.2)) {df3[j,i+1]=1}
		}
	  }
	}

![Libre Office with the outcoming file](/images/Posts/2021/2021-06-12_Image4.png){: .center-image }

And we can end up by writing this file into a CSV that we can open with your favourite calc sheet programs. 

	write.table(df3, file = r"(B:\Documentos\GitHub\RMusicOrganiser\Artist_Genre.csv)",
				sep = ",",
				row.names = FALSE)

From here, there is a lot of listening to the music, assign a genre, rinse and repeat. Several months later, if you manage to finish this task instead of playing the three Mass Effect games in a row (cough..., cough...), you would need to update the original tracklist.csv. Update the genre column with your new genres, and use TagScanner to import the information into the library. Hence the importance of not updating, adding or removing songs, or the whole process would be screwed.
