---
layout: post
title: Go Challenge - 9
tags: [go challenge, golang]
---

#### The July 2016 Go Challenge for developers (newbies included)

#### Aaron Cruz: Author of the 9th Go Challenge

<img align="right" src="/images/aaron-cruz.png" height="200" width="200" alt="Aaron Cruz" title="Aaron Cruz" style="border:5px solid black" />
The 9th Go Challenge author, Aaron Cruz, is a food lover who speaks about Go and other programming languages at conferences around the world. For his real job, he helps marketplaces start making revenue faster by integrating with Stripe Connect to simplify buyer/seller (rider/driver, freelancer/client) payments.

Aaron has this to say about the challenge:

> "I am interested in a pragmatic approach and I want the entrant to have fun. It doesn’t need to be exact, just as accurate as you can get. Cut corners and break rules if you need to :)"

--- 

#### The Go Challenge 9

##### Nothin' But a Go Thang

##### Preamble

I grew up with Hip Hop. It connected me with a culture that seemed very alien, having grown up in the suburb of a suburb in Northwestern USA. Hip Hop changed dramatically over the years but one thing that stayed constant was story telling.

Here are some samples of some of my favorites over the decades starting from my youth to the present.

80s <a href="https://www.youtube.com/embed/2TN-kDEKxF0">Eric B. & Rakim - I Ain't No Joke</a>

90s <a href="https://youtu.be/_JZom_gVfuw">The Notorious B.I.G. - "Juicy"</a>

00s <a href="https://youtu.be/UVtpXvzzXiA">Talib Kweli - Get By</a>

10s <a href="https://youtu.be/R3ib9gCw1F4">Open Mike Eagle - Ziggy Starfish</a>

It has always been one of my dreams to be a rapper. Unfortunately I spend way too much time on Twitter. I don’t have nearly the amount of time and energy necessary to write rhymes and practice my flow.

**The Goal of the challenge**

The goal of this challenge is to create a tweet to rap converter. It will take a twitter user as input and return rap versions of the tweets in their timeline.

**Requirements of the challenge**

For example, let’s take Brad Fitz tweet:

> I've never used Plan 9, but I watch it install occasionally.
> And today I learned that "myriad" can mean 4. <a href="pic.twitter.com/sIkvgEBMEF">pic.twitter.com/sIkvgEBMEF</a>
>
> — Brad Fitzpatrick (@bradfitz) <a href="https://twitter.com/bradfitz/status/729875418837196800">May 10, 2016</a>

One possible output could be...

Leave you, I never mean to<br />I watch it occasionally<br />Today I learned what I’m about to do

Or from Mr. Cheney:

> Companies that reject remote working are implicitly putting their own internal communication problems above hiring the best candidate.
>
> — Dαve Cheney (@davecheney) <a href="https://twitter.com/davecheney/status/599404180483284993">May 16, 2015</a>

Could be...

Workin’ with the work, plus you know I keep the strap!<br />Problem is communication just be between me and myself<br />back to the snap

**Features**:

* Tweets are 140 characters or less
* two lines need to rhyme
* it feels as much as possible like the original tweet

**Hint**

* Take a look at the Soundex and Metaphone algorithms

**Bonus features**:

* keep a nice meter
* complex rhyming scheme (ex. multi-sylable rhymes)
* classic hip hop lyrics mixed in

---

#### Challenge Rules and how to enter the Go Challenge?

By participating in this challenge, you agree to be bound by the Challenge Rules below:

* The Challenge is open to individuals.
* Evaluators cannot enter the challenge except under the "Just for Fun" category.
* Each entrant shall indemnify, defend, and hold JoshSoftware Pvt. Ltd. (who has sponsored the domain and is the organizer of these challenges) harmless from any third party claims arising from or related to that entrant's participation in the Challenge. In no event shall JoshSoftware Pvt. Ltd. be liable to an entrant for acts or omissions arising out of or related to the Challenge or that entrant's participation in the Challenge.
* Odds of winning depend on the number and quality of entries received. 
* All taxes, including income taxes, are the sole responsibility of the winners. 
* No prize substitution is permitted.
* Create a zip of your Go source code and test cases and send the zip file to **golangchallenge [at] gmail.com before 24th of July 2016 (6 am IST)**. Use [this link](http://www.worldtimeserver.com/convert_time_in_IN.aspx?y=2016&mo=7&d=24&h=6&mn=0) to find the equivalent time in your city/country. No new solutions will be accepted after that. In the email mention **your full name, country of residence, twitter or GitHub id (if any) and participating under which category - Just participating or Participating and exploring further or Just for Fun or Anonymous entry**. We are accepting anonymous submissions and will evaluate them too but then these participants are not eligible for the prizes. 
* We shall be publishing on this blog, a list of participant names. If you don't want your name to appear kindly mention the same in your email. 
* You are allowed to re-submit your code if you feel it is necessary.
* After the challenge is over, all submissions will be made available [online on GitHub](https://github.com/golangchallenge/GCSolutions) under the [BSD 3-Clause License](http://opensource.org/licenses/BSD-3-Clause) or the [GNU General Public License, version 3 - GPL-3.0](http://opensource.org/licenses/GPL-3.0) unless a participant has indicated that his/her solution should not be made public before the challenge ends.

#### How will the challenge be evaluated?

Entries will be evaluated by the challenge author and a team of evaluators.

#### Questions?

If you have any questions about this challenge, please join the [golang-challenge channel on slack](http://t.co/n6EesY9Mmv) and ask your questions. This is a room for people who are going to participate in the Go Challenge. You can also send us an email at golangchallenge [at] gmail.com

<!--
#### Evaluators

[Nathan Youngman](https://twitter.com/nathany) had set the guidelines for evaluation for the first Go Challenge. Subsequently [Dominik Honnef](https://twitter.com/dominikhonnef) modified the guidelines based on his experience as an evaluator for the first challenge. [Austin Riendeau](https://github.com/apriendeau), [Cory LaNou](https://twitter.com/corylanou), [Edd Robinson](https://github.com/e-dard), [Gautam Dey](https://github.com/gdey), [Jyotiska NK](https://twitter.com/jyotiska_nk), [Kevin Gillette](https://twitter.com/kevingillette) and [Pravin Mishra](https://twitter.com/pravinmishra88) have agreed to go through all the submitted solutions of a challenge. They will comment and rank these solutions.
-->

#### Best Solution

The author of the Go Challenge will decide the best two solutions. The author shall have the sole authority and discretion to select the award recipients. 

#### Notification

The winning entries will be announced here on this blog. The winners will be sent their prizes by email/postal mail.

#### Prizes

The author of the challenge will select 2 winners and prizes will be awarded to them.

Here are some great prizes provided by our sponsors for the event.

_Winner 1_:

* [Apcera](https://www.apcera.com/) - [Go Gopher Squishable](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [Cube Root Software](http://cuberoot.in/) - An eBook [Functional Programming for the Object-Oriented Programmer](https://leanpub.com/fp-oo)
* [GitHub](https://github.com/) - A [Micro Personal Plan](https://github.com/pricing)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)

_Winner 2_:

* [Apcera](https://www.apcera.com/) - [Go Gopher Squishable](https://www.googlemerchandisestore.com/shop.axd/Search?keywords=gopher)
* [GitHub](https://github.com/) - A [Micro Personal Plan](https://github.com/pricing)
* [Qwinix Technologies](http://www.qwinixtech.com/) - An eBook [The Docker Book: Containerization is the new virtualization](http://goo.gl/6sJJTy)

#### Challenge Solutions

All the solutions submitted by the participants will be available **[here](https://github.com/golangchallenge/GCSolutions)** after the challenge ends.

#### Sponsors

This challenge's sponsors are: [Apcera](https://www.apcera.com/), [Cube Root Software](http://cuberoot.in/), [GitHub](https://github.com/), [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/) and [Qwinix Technologies](http://www.qwinixtech.com/).

#### Credit

* The Gopher character is based on the Go mascot designed by Renée French and copyrighted under the Creative Commons Attribution 3.0 license.
* [GitHub](https://github.com/) for the yearly sponsorship of a [GitHub Bronze Organisation plan](https://github.com/pricing) for the Go Challenge.
* The Go Challenge is being organized by [JoshSoftware Pvt. Ltd.](http://www.joshsoftware.com/) with help from the Go community.
