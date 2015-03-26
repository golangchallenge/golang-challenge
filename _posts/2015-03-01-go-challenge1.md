---
layout: post
title: Go Challenge 1
tags: [go challenge, golang]
---

#### The world's first monthly Go Challenge for developers (newbies included)

--- 

![update.jpg](/images/update.jpg)

* This first Go challenge is now closed.
* There were 173 entries from 41 countries.
* The winners of the first Go Challenge are: [Luke Champine](https://twitter.com/NebulousLabs) and [Jeremy Jay](https://github.com/pbnjay).

* The (#2) challenge by **Guillaume J. Charmes** is scheduled for 1st Apr. 2015.

**Feedback from the Evaluators**

> Difficult to give generalized comments, but here are some suggestions.
>
> 1. Running `go vet` and `golint` should be a no-brainer. I found that a few entries failed this test.
> 2. Use the `defer` statement to free up resources after use - for example, on file open.
> 3. Do not over-engineer. Types are easy to define, but sometimes, all you need is a func.
> 4. Comment your code well. What may seem obvious to you may not be so obvious to someone reading your code.

A more detailed feedback is available [here](http://golang-challenge.com/evaluator-feedback/).

--- 

#### Matt Aimonetti: Author of the first Go Challenge

<img align="right" src="/images/m_aimonetti.jpg" height="200" width="200" alt="Matt Aimonetti" title="Matt Aimonetti" style="border:5px solid black" />
The first Go Challenge author is [Matt Aimonetti](http://matt.aimonetti.net/), CTO and co-founder of [Splice](https://splice.com/), a technology platform for music creators. Splice streamlines the fragmented process of creating and sharing music, freeing musicians to spend their time and energy on the creative process. 

Long before Splice, Matt was a former sound engineer who tried his hand as an artist before transitioning to full time programming, working for companies such as Sony PlayStation and LivingSocial. Matt has been active in the Open Source community for many years, developing or contributing to many projects (Merb, Rails, MacRuby and many more). He also wrote a [free book about Go](http://www.golangbootcamp.com/) and is a [published tech author](http://www.oreilly.com/pub/au/4385) for O'Reilly. Matt is based in Santa Monica, California.

Matt has this to say about the challenge:

> "Very often developers just need an excuse to learn a new language or develop their own skills. The Go challenge is a great opportunity to work on a low-pressure, isolated, fun challenge and hopefully learn a lot. Getting out of the day to day programmer routine is an awesome way to challenge your brain and become a better developer."

--- 

#### The Go Challenge 1

This morning I took my daughter Giana to my secret lab to show her the various inventions I built over the years. That's when I realized that the awesome drum machine prototype I designed in the 90s had disappeared!!! The only related things I could find were printouts of the patterns I had created on the device as well as backups saved on floppy disks. Here are the printed patterns:

```
pattern_1.splice
Saved with HW Version: 0.808-alpha
Tempo: 120
(0) kick     |x---|x---|x---|x---|
(1) snare    |----|x---|----|x---|
(2) clap     |----|x-x-|----|----|
(3) hh-open  |--x-|--x-|x-x-|--x-|
(4) hh-close |x---|x---|----|x--x|
(5) cowbell  |----|----|--x-|----|
```

```
pattern_2.splice
Saved with HW Version: 0.808-alpha
Tempo: 98.4
(0) kick    |x---|----|x---|----|
(1) snare   |----|x---|----|x---|
(3) hh-open |--x-|--x-|x-x-|--x-|
(5) cowbell |----|----|x---|----|
```

```
pattern_3.splice
Saved with HW Version: 0.808-alpha
Tempo: 118
(40) kick    |x---|----|x---|----|
(1) clap     |----|x---|----|x---|
(3) hh-open  |--x-|--x-|x-x-|--x-|
(5) low-tom  |----|---x|----|----|
(12) mid-tom |----|----|x---|----|
(9) hi-tom   |----|----|-x--|----|
```

```
pattern_4.splice
Saved with HW Version: 0.909
Tempo: 240
(0) SubKick	      |----|----|----|----|
(1) Kick	      |x---|----|x---|----|
(99) Maracas	  |x-x-|x-x-|x-x-|x-x-|
(255) Low Conga	  |----|x---|----|x---|
```

```
pattern_5.splice
Saved with HW Version: 0.708-alpha
Tempo: 999
(1) Kick	|x---|----|x---|----|
(2) HiHat	|x-x-|x-x-|x-x-|x-x-|
```

I need your help to reverse engineer the binary format used by my drum machine and write a decoder so I will be able to implement a new drum machine, using Go this time!

#### To get started

You will find [attached a zip file](/data/ch1/golang-challenge-1-drum_machine.zip) containing the starting point for this challenge.
Your goal is to implement the `drum` package and make it pass the
provided tests.

#### Some information about my legacy drum machine

My drum machine loads an audio sample per track, allowing the programmer to schedule the playback of the sound. The scheduling of the playback is done using the concept of steps. A step is one of the parts of the measure that is being programmed (the programmed measure is known as a pattern). The measure (also called a bar) is divided in steps.

![measure.png](/images/measure.png)

My drum machine only supports 16 step measure patterns played in 4/4 time. The measure is comprised of 4 quarter notes, each quarter note is comprised of 4 sixteenth notes and each sixteenth note corresponds to a step.
If all these music terms are confusing, don't worry, just know that the drum machine uses grid of 16 parts to let you trigger a sound. We have one sound per track and each track can be programmed independently. Each part is called a step. The speed of the playback is based on the tempo (aka bpm).

Taking an example from the printouts above:
```
(40) kick |x---|----|x---|----|
```

means that we have a track called "kick" (id 40) with the sound output being triggered on the first and ninth steps.

#### Goal

The goal of this challenge is to write a binary decoder that given a binary backup, outputs the same printouts as shown above. To do that you need to implement the `DecodeFile(path string) (*Pattern, error)` function inside the drum package. Note that `*Pattern` needs to be printable so it can be compared to the printouts. To help you, a test is provided. To run the test suite, use your terminal to navigate to the location of the unzip file and run `go test -v`. You should see an output similar to this:

```
go test -v
=== RUN TestDecodeFile
--- FAIL: TestDecodeFile (0.00s)
	decoder_test.go:69: decoded:
		"&{}"
	decoder_test.go:70: expected:
		"Saved with HW Version: 0.808-alpha\nTempo: 120\n(0) kick\t|x---|x---|x---|x---|\n(1) snare\t|----|x---|----|x---|\n(2) clap\t|----|x-x-|----|----|\n(3) hh-open\t|--x-|--x-|x-x-|--x-|\n(4) hh-close\t|x---|x---|----|x--x|\n(5) cowbell\t|----|----|--x-|----|\n"
	decoder_test.go:72: pattern_1.splice wasn't decoded as expect.
		Got:
		&{}
		Expected:
		Saved with HW Version: 0.808-alpha
		Tempo: 120
		(0) kick	|x---|x---|x---|x---|
		(1) snare	|----|x---|----|x---|
		(2) clap	|----|x-x-|----|----|
		(3) hh-open	|--x-|--x-|x-x-|--x-|
		(4) hh-close	|x---|x---|----|x--x|
		(5) cowbell	|----|----|--x-|----|
FAIL
exit status 1
```

#### Requirements

* Only use Go standard library. No third-party libraries may be imported.
* You are welcome to modify (improve) the included test suite or move the binaries, but the `DecodeFile` API must remain and the original test suite must still pass.

#### Hints

* Look around to see how data is usually [serialized/encoded](http://golang.org/pkg/encoding/json/).
* Become familiar with [encoding/binary package](http://golang.org/pkg/encoding/binary/), especially [binary.Read](http://golang.org/pkg/encoding/binary/#Read).
* [hex.Dump](http://golang.org/pkg/encoding/hex/#Dump) can very useful when debugging binary data (read more about [hex dump](http://en.wikipedia.org/wiki/Hex_dump))

#### I don't know where to start :(

<a href="/images/hex.png"><img src="/images/hex.png" width="627" alt="Hex Viewer" title="Hex Viewer" style="border:0px"></a>

The first step is to reverse engineer the binary file format. Look at the hex values to see if you can detect patterns. Binary data usually contains some sort of headers, then the encoded data. You should expect to find the data described in the printouts:

* version
* tempo
* tracks with each track containing
  * id
  * name
  * 16 steps

Then you need to write a decoder that takes one of the provided binary files and extracts/prints the data.

#### Go further (optional, not evaluated for the challenge)

This advanced section is not for the faint of heart, in case you were about to complain about how easy this challenge was, or if you just want to push things further, here is some more!

How about editing the cowbell track to add more steps? Reading the binary format is one thing, being able to generate/modify the data is even more fun. Take a pattern of your choosing and add more cowbell! For instance convert `pattern_2.splice` from:

```
pattern_2.splice
Saved with HW Version: 0.808-alpha
Tempo: 98.4
(0) kick    |x---|----|x---|----|
(1) snare   |----|x---|----|x---|
(3) hh-open |--x-|--x-|x-x-|--x-|
(5) cowbell |----|----|x---|----|
```

to:

```
pattern_2-morebells.splice
Saved with HW Version: 0.808-alpha
Tempo: 98.4
(0) kick    |x---|----|x---|----|
(1) snare   |----|x---|----|x---|
(3) hh-open |--x-|--x-|x-x-|--x-|
(5) cowbell |x---|x-x-|x---|x-x-|
```

Still not enough? Why not implementing the playback of the patterns
using something like [portaudio](https://godoc.org/code.google.com/p/portaudio-go/portaudio)?

---

#### Challenge Rules and how to enter the Go Challenge?

By participating in this challenge, you agree to be bound by the Challenge Rules below:

* The Challenge is open to individuals.
* After the challenge, all submissions will be made available online on GitHub under the [BSD 3-Clause License](http://opensource.org/licenses/BSD-3-Clause).
* Evaluators cannot enter the challenge except under the "Just for Fun" category.
* Each entrant shall indemnify, defend, and hold JoshSoftware Pvt. Ltd. (who has sponsored the domain and is the organizer of these challenges) harmless from any third party claims arising from or related to that entrant's participation in the Challenge. In no event shall JoshSoftware Pvt. Ltd. be liable to an entrant for acts or omissions arising out of or related to the Challenge or that entrant's participation in the Challenge.
* Odds of winning depend on the number and quality of entries received. 
* All taxes, including income taxes, are the sole responsibility of winners. 
* No prize substitution is permitted. 
* Create a zip of your Go source code and send the zip file to **gochallenge [at] joshsoftware.com by the 13th of March 2015 (6 am IST). Use [this link](http://www.worldtimeserver.com/convert_time_in_IN.aspx?y=2015&mo=3&d=13&h=6&mn=0) to find the equivalent time in your city/country**. No new solutions will be accepted after that. In the email mention **your full name, country of residence, and twitter id (if any)**. We shall be publishing on this blog, a list of participant names. If you don't want you name to appear kindly mention the same in your email. We are accepting anonymous submissions and will evaluate them too but then these participants are not eligible for the prizes. We will give your zip file to the evaluation team. **Note**: Avoid sharing your code with anyone else; if your solution becomes available to the general public it might impact evaluation of your submission.

#### How will the challenge be evaluated?

Entries will be anonymized and evaluated by the challenge author and a team of evaluators.

* Functioning code and a test suite that passes.
* Code hygiene. Use [gofmt](https://golang.org/cmd/gofmt/), [vet](https://godoc.org/golang.org/x/tools/cmd/vet) and [lint](https://github.com/golang/lint). Review [CodeReviewComments](https://code.google.com/p/go-wiki/wiki/CodeReviewComments).
* Readability. How easy is it for another programmer to grasp what your entry is doing?
* Code structure. Do types and files have good names?
* Reliability. Are errors properly handled?
* Appropriate consideration given to memory and performance (nothing is unnecessarily expensive).

#### Questions?

If you have any questions about this challenge, please join the [golang-challenge channel on slack](http://t.co/n6EesY9Mmv) which is a room for people who are going to participate in the Go Challenge.

#### Evaluators

[Nathan Youngman](https://twitter.com/nathany) has agreed to set the guidelines for evaluation. [Dominik Honnef](http://dominik.honnef.co/), [Guillaume J. Charmes](https://twitter.com/charme_g), [Jiahua Chen](https://twitter.com/joe2010xtmf), [Niket Patel](https://twitter.com/nexneo), [Pravin Mishra](https://twitter.com/pravinmishra88) and [Sanat Gersappa](https://twitter.com/sanatgersappa) have agreed to go through all the submitted solutions of a challenge. They will comment and rank these solutions.

#### Best Solution

The author of the Go Challenge will decide the best two solutions. The author shall have the sole authority and discretion to select the award recipients. 

#### Notification

The winning entries will be announced here on this blog. The winners will be sent their prizes by email/postal mail.

#### Prizes

Two prizes will be awarded for the best solution as selected by the author.

Here are some great prizes provided by our sponsors for the event.

_Winner 1_:

* [Anand D N](https://twitter.com/Wanderer140) - [Essential-Go screencast](https://www.kajabinext.com/marketplace/courses/1-essential-go)
* [Apcera](https://www.apcera.com/) - [Go Gopher Messenger Bag](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [CoreOS](https://coreos.com/) - Company T-Shirt and stickers and a free ticket to the [CoreOS Fest](https://coreos.com/fest/) in SFO.
* [Crowd Interactive](http://www.crowdint.com/) - [GitHub Micro Personal Plan](https://github.com/pricing) for three months
* [Cube Root Software](http://cuberoot.in/) - An eBook [Go-The Standard Library](https://leanpub.com/go-thestdlib)
* [DigitalOcean](https://www.digitalocean.com/) - US$ 50 Amex Gift Card
* [Helpshift](http://www.helpshift.com/) - An eBook [A Go Developer's Notebook](https://leanpub.com/GoNotebook)
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [John Sonmez](https://twitter.com/jsonmez) - An eBook [Soft Skills: The software developer's life manual](http://www.amazon.com/gp/product/1617292397/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=1617292397&linkCode=as2&tag=satishtalimsw-20&linkId=WGSAUMHIF2SVWJ7D)
* [Koding](https://koding.com/Pricing) - A free Hobbyist plan for 3 months
* [Manning Publications Co.](http://manning.com/) - Two eBooks [Go Web Programming](http://www.manning.com/chang/) and [Go in Action](http://www.manning.com/ketelsen/)
* [NodePrime](http://www.nodeprime.com/) - An eBook [The Go Programming Language Phrasebook (Developer's Library)](http://goo.gl/mTwIOS)
* [O'Reilly](http://www.oreilly.com/) - An eBook [Introduction to Go Programming](http://shop.oreilly.com/product/0636920035305.do)
* [Packt Publishing](https://www.packtpub.com/) - A print book [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [RainingClouds](http://rainingclouds.com/#!/) - An eBook [Level Up Your Web Apps With Go](http://shop.oreilly.com/product/9780992461294.do)
* [SoStronk](https://www.sostronk.com/) - [Counter-Strike: Global Offensive](http://store.steampowered.com/app/730/) game. You will need to have a free [Steam account](https://store.steampowered.com/join/?) to receive this gift.
* [Sourcegraph](https://sourcegraph.com/) - [Interview with the winner on their blog and will get their shirt, stickers](https://sourcegraph.com/blog)

_Winner 2_:

* [Anand D N](https://twitter.com/Wanderer140) - [Essential-Go screencast](https://www.kajabinext.com/marketplace/courses/1-essential-go)
* [Apcera](https://www.apcera.com/) - [Go Gopher Squishable](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [CoreOS](https://coreos.com/) - Company T-Shirt and stickers and a free ticket to the [CoreOS Fest](https://coreos.com/fest/) in SFO.
* [Crowd Interactive](http://www.crowdint.com/) - [GitHub Micro Personal Plan](https://github.com/pricing) for three months
* [DigitalOcean](https://www.digitalocean.com/) - US$ 50 Amex Gift Card
* [Docker](https://www.docker.com/) - A ticket to [DockerCon 2015](http://www.dockercon.com/) in SFO, USA OR to DockerCon Europe (to be announced but probably in Dec. 2015).
* [Helpshift](http://www.helpshift.com/) - An eBook [A Go Developer's Notebook](https://leanpub.com/GoNotebook)
* [InfluxDB](http://influxdb.com/) - A US$ 50 Amazon digital gift card.
* [John Sonmez](https://twitter.com/jsonmez) - An eBook [Soft Skills: The software developer's life manual](http://www.amazon.com/gp/product/1617292397/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=1617292397&linkCode=as2&tag=satishtalimsw-20&linkId=WGSAUMHIF2SVWJ7D)
* [Koding](https://koding.com/Pricing) - A free Hobbyist plan for 3 months
* [Manning Publications Co.](http://manning.com/) - Two eBooks [Go Web Programming](http://www.manning.com/chang/) and [Go in Action](http://www.manning.com/ketelsen/)
* [NodePrime](http://www.nodeprime.com/) - An eBook [The Go Programming Language Phrasebook (Developer's Library)](http://goo.gl/mTwIOS)
* [Packt Publishing](https://www.packtpub.com/) - An eBook [Building Your First Application with Go-Video](https://www.packtpub.com/application-development/building-your-first-application-go-video)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)
* [RainingClouds](http://rainingclouds.com/#!/) - An eBook [Level Up Your Web Apps With Go](http://shop.oreilly.com/product/9780992461294.do)
* [SoStronk](https://www.sostronk.com/) - [Counter-Strike: Global Offensive](http://store.steampowered.com/app/730/) game. You will need to have a free [Steam account](https://store.steampowered.com/join/?) to receive this gift.
* [Sourcegraph](https://sourcegraph.com/) - [Interview with the winner on their blog and will get their shirt, stickers](https://sourcegraph.com/blog)

Anyone can a get 42% off on the price of the following eBooks from [Manning Publications Co.](http://manning.com/):

* [Go Web Programming](http://www.manning.com/chang/) - Use discount code: **cftw15go**
* [Go in Action](http://www.manning.com/ketelsen/) - Use discount code: **cftw15go**

Also, anyone can a get 25% off on the price (valid till 31st March 2015) of the following print and / or eBooks from [Packt Publishing](https://www.packtpub.com/):

* [Building Your First Application with Go-Video](https://www.packtpub.com/application-development/building-your-first-application-go-video) - Use discount code: **byfag25**
* [Mastering Concurrency in Go](https://www.packtpub.com/application-development/mastering-concurrency-go) - Use discount code: **giccm25**
* [Go Programming Blueprints](https://www.packtpub.com/application-development/go-programming-blueprints) - Use discount code: **bgpg25**

#### Winner Interviews

After a winner wins the monthly challenge, he/she would be interviewed by [Sourcegraph](https://sourcegraph.com/) and the interview will be published on their [blog](https://sourcegraph.com/blog).

#### The Participants

<p>You can check out the list of participants for this challenge i.e. for <a href="{{ site.baseurl }}/participants/march15">March 2015</a>.</p>

#### Challenge Solutions

All the solutions submitted by the participants are available **[here](https://github.com/golangchallenge/GCSolutions)**.

#### The Winners

![winner.png](/images/winner.png)

Matt Aimonetti has selected the winners of this challenge. They are:

<img align="right" src="/images/luke.jpg" alt="Luke Champine" title="Luke Champine" style="border:5px solid black" />
**Winner #1 Luke Champine** never expected to wind up as a programmer; in college he first studied electrical engineering, and then computer engineering. But he got involved in his school's open source community, which sparked his love of programming and introduced him to Go. He left school without graduating and moved to Boston to co-found [Nebulous](https://twitter.com/NebulousLabs), a cryptocurrency startup. 

Outside of programming, his interests include linguistics, Buddhism, and chess.

His [solution](https://github.com/golangchallenge/GCSolutions/tree/master/march15/normal/luke-champine) to the challenge.

--- 

<img align="right" src="/images/jeremy.jpg" alt="Jeremy Jay" title="Jeremy Jay" style="border:5px solid black" />
**Winner # 2 Jeremy Jay** has been a developer for almost 20 years now. He earned his PhD in Computer Science in 2013, and runs a freelance [software development company](http://stridatum.com/) specializing in mobile apps and complex data integration projects (which often go together!). He has developed applications for all 5 major Operating Systems (Linux, OSX, Windows, iOS, Android), some smaller/embedded ones, using the myriad languages he had picked up along his career. Go is by far his favorite, and has become his daily driver, even for things he used to write short python scripts for. Go's brevity and expressiveness makes it extremely versatile for his daily work.

His [solution](https://github.com/golangchallenge/GCSolutions/tree/master/march15/extra/jeremy-jay/stridatum-go-challenge-1-8f32f9a76497) to the challenge.

--- 

Matt also mentioned that **Doug Cichon** was a very close #2.

#### Sponsors

This challenge's sponsors are: [Anand D N](https://twitter.com/Wanderer140), [Apcera](https://www.apcera.com/), [CoreOS](https://coreos.com/), [Crowd Interactive](http://www.crowdint.com/), [Cube Root Software](http://cuberoot.in/), [DigitalOcean](https://www.digitalocean.com/), [Docker](https://www.docker.com/), [GopherCasts](https://gophercasts.io/), [Helpshift](http://www.helpshift.com/), [InfluxDB](http://influxdb.com/), [John Sonmez](https://twitter.com/jsonmez), [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/), [Manning Publications Co.](http://manning.com/), [NodePrime](http://www.nodeprime.com/), [O'Reilly](http://www.oreilly.com/), [Packt Publishing](https://www.packtpub.com/), [Qwinix Technologies](http://www.qwinixtech.com/), [RainingClouds](http://rainingclouds.com/#!/), [SoStronk](https://www.sostronk.com/) and [Sourcegraph](https://sourcegraph.com/).

#### Credit

* The Gopher character is based on the Go mascot designed by Renée French and copyrighted under the Creative Commons Attribution 3.0 license.
* The Go Challenge is being organized by [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/) with help from the Go community.
