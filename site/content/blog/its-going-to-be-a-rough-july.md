+++
title = "Its Going to Be a Rough July"
date = "2018-04-26T14:22:17+08:00"
tags = ["Sentiment","Tableau","Collaboration"]
categories = ["Analysis"]
banner = "img/banners/banner-1.jpg"
+++

There are plenty of ways one can go about analyzing the rich recesses in Trumps Twitter archives. Tim, and I wanted to see if sentiment analysis would turn up anything useful. In this short post, we share what was found.

In April 2016, the media repeatedly reported on [Trump's warning of a rough July](http://fortune.com/2016/04/18/donald-trump-rough-july/). Trump went so far as to say there could be riots at the Republican National Convention if things didn’t go his way. You mess with Trump's campaign you mess with his staunch supporters.

![](/img/post-1/trump-yelling.png)

To be honest, I don’t follow politics closely. These reports and threats were new news. What drew my attention to this tense period in history was the sentiment (read: emotion) in Trump’s tweets during July 2016.

![](/img/post-1/area-chart.png)
</iframe>
  <div class='tableauPlaceholder' id='viz1524741612356' style='position: relative'>
    <noscript>
      <a href='#'>
        <img alt='MM Week 03 ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;wo&#47;workbook_26&#47;MMWeek03&#47;1_rss.png' style='border: none' />
      </a>
    </noscript>
    <object class='tableauViz'  style='display:none;'>
      <param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' />
      <param name='embed_code_version' value='3' />
      <param name='site_root' value='' />
      <param name='name' value='workbook_26&#47;MMWeek03' />
      <param name='tabs' value='no' />
      <param name='toolbar' value='yes' />
      <param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;wo&#47;workbook_26&#47;MMWeek03&#47;1.png' />
      <param name='animate_transition' value='yes' />
      <param name='display_static_image' value='yes' />
      <param name='display_spinner' value='yes' />
      <param name='display_overlay' value='yes' />
      <param name='display_count' value='yes' />
    </object>
  </div>
  <script type='text/javascript'>
    var divElement = document.getElementById('viz1524741612356');
    var vizElement = divElement.getElementsByTagName('object')[0];                    vizElement.style.width='625px';vizElement.style.height='627px';
    var scriptElement = document.createElement('script');
    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';                    vizElement.parentNode.insertBefore(scriptElement, vizElement);
  </script>
</iframe>

> Sentiment analysis (sometimes known as opinion mining or emotion AI) refers to the use of natural language processing, text analysis, computational linguistics, and biometrics to systematically identify, extract, quantify, and study affective states and subjective information. — Wikipedia: Sentiment Analysis

Sentiment analysis is the computational process Timo and Robo used to pull out the views or options held in his tweets. You can imagine why this is a powerful method to apply to text heavy social media sites like Twitter and Facebook. Take a bunch of tweets from a guy like Trump, and you’re sure to see some extreme spikes across the spectrum of sentiment.

While sentiment analysis is useful, it hasn’t yet evolved to a point where we can capture all the nuanced emotions of our text. To keep the analysis simple and clear, we divided the compound score* into three categories; negative was less than 0% (on a -100% to 100% scale), positive if the tweet had a score higher than 0% and neutral when it equaled 0.

![](/img/post-1/sentiment-calculation.png)

Our sentiment analysis shows that July 2016 is the first point where positive sentiment fell below 50%.

![](/img/post-1/low-positivity.png)

Trump said it would be a rough July, but I doubt he knew just how rough. The United States experienced a series of civilian attacks on police officers and saw terrorism in Florida as well as Nice, France.

What can you reveal in your Tweets or that of your company? Heck, take this analysis and compare it to another active tweeter to see how their sentiment varies. What sort of opinions are new agencies promoting versus universities versus sports team with winning records versus those with losing records?

The questions are endless. Get creative. Have fun!

---

## References & Mentions

Timo loves to talk about sentiment analysis.  You can hit him up at [timothylombard@gmail.com](mailto:http://timothylombard@gmail.com)

Stories that unfolded in July 2016:

* [Nice Attack](https://en.wikipedia.org/wiki/2016_Nice_attack )
* Other stories mentioned by [infoplease](https://www.infoplease.com/world/2016-current-events/july-2016-current-events-us-news-slideshow)

According to the [README](https://github.com/cjhutto/vaderSentiment) file for the [vaderSentiment module](https://github.com/cjhutto/vaderSentiment), “The compound score is computed by summing the valence scores of each word in the lexicon, adjusted according to the rules, and then normalized to be between -1 (most extreme negative) and +1 (most extreme positive). This is the most useful metric if you want a single unidimensional measure of sentiment for a given sentence. Calling it a 'normalized, weighted composite score' is accurate.”