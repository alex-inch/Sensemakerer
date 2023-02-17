# Sensemakerer
Fine-tuning GPT-3 to write newsletters

- [The Sensemakerer](#the-sensemakerer)
  - [About the Project](#about-the-project)
  - [Files](#files)
    - [`data_production.ipynb`](#data_productionipynb)
    - [`api_calls.ipynb`](#api_callsipynb)
  - [Example Outputs](#example-outputs)
  - [Notes](#notes)

## About the Project
This is a short, hacky project that uses email newsletters (Tortoise's [Daily Sensemaker](https://www.tortoisemedia.com/sensemakers/)) to fine tune a GPT-3 (`davinci`) model.

This model can then produce newsletters using an email subject as the prompt.

## Files
There are two main Jupyter notebooks:

### `data_production.ipynb`
1. Reads an email inbox (I produced it using Google Takeout).
2. Cleans up the data.
3. Produces the fine-tuning data in the appropriate `.jsonl` format.
4. Runs the bash commands using the OpenAI API to fine-tune an instance of davinci.

### `api_calls.ipynb`
1. Defines utility functions to produce and render api calls to fine-tuned models.
2. Contains logic to save function calls to a local `.pkl` file.

## Example Outputs
Some example outputs from the Sensemakerer (with minor added formatting)

> ### Japan wins big at Olympics
<details>
  <summary>Read output</summary>

**Japan wins big at Olympics.** This could become Japan’s gold medal summer. Team Japan struck gold for the first time at the Paralympics in Tokyo on Saturday. There will be further opportunities to pinch their medals at the Winter Olympics, which start next week, and at the World Cup in Qatar in 2022. Then there are the chances to bid for the 2026 World Cup – and win.

Japan already leads the world in robots and one-seeds in tennis, but there’s more:

- **Not just tinpot.** Japan’s bid to host the football World Cup was hailed as wonderfully simple at a time when other bids were elaborate and oddly coordinated. It won in a landslide and its chances of staging an excellent tournament are good to excellent.
- **Cross training.** The Japanese men’s wheelchair basketball team have been training for the Paralympics for six years.
- **Coming through.** The player with the most goals in Paralympic football is Yuta Nakashima, a 34-year-old with cerebral palsy who was persuaded to go to a training camp at 17.

That brings us back to the Olympics, and a lesson in how to make it in sports as a young person. "My parents told me I could go [to the training camp],” Nakashima told the New York Times. "So I went – but only to watch. When I got there, the coaches persuaded me to play, saying ‘let’s give it a try’. I’m glad I listened.”

The camp was for potential Paralympic players. Nakashima went on to score a hat trick in his third tournament for Japan. This year he led the race for top goalscorer with 17 in six games.

A note on the Japanese team in Doha: there are no quotas or extra funding for the country’s disabled players. They’re all athletes, period, picking themselves to represent the land of the rising sun. Nineteen-year-old Musashi Mizuno already has 10 Paralympic medals, while in the over-16s group the team includes a 72-year-old goalkeeper who used to play for Brazil.

**The samba beat.** In Tokyo last month, Team GB’s Chef de Mission Liz McCollel said the UK was “not in the same league”  

</details>


> ### Asteroid lights up sky

<details>
  <summary>Read output</summary>

**Asteroid lights up sky**. It looks like a point of light. Planet-bound, 400 times the distance between the Earth and the Sun, it’s officially known as asteroid 4569 Belem. Last night, it blazed through the night sky in an unannounced act of celestial performance art: the Space Hopper.

**What?** The hoop of light – caused by the reflection of light from the asteroid’s surface – was spotted from Arizona by a photographer shooting the Orionid meteor shower. It’s unlikely to be a hoax, but there’s still plenty for sceptics to scoff at:
- **Silly name.** The Hopper is well-established among amateur astronomers and has been observed since 1999, but its title recalls a quip made by the former US defence secretary William Cohen: when it comes to stopping asteroids, we just don’t have a cow big enough.
- **Other cows.** In 2017, Donald Trump’s habit of re-tweeting fake news (well, news he found interesting) led to the creation of his very own space rock, orbiting the Sun between the Asteroids and Jupiter. It was christened after his hairstyle, the ‘Flippy Doo’.
- **The plot thickens.** Some believe Earth was hit by a slow-moving asteroid about 6,000 years ago. Some believe it was hit by a slow-moving planet. “We can neither confirm nor deny that Hubert Mars, great-grandfather of Augustus, was in fact Hubert Asteroid,” Alan Toner, a self-described mythologist, tells the Times.

**Indirect threats**. There’s a worrying discrepancy between how many asteroids, large and small, we can track from Earth and how many we can intercept. We can track a lot. We can shoot at a select few, but not soon enough to prevent a devastating impact. So a team of technologists has been creating methods to deflect or shield Earth from incoming asteroids. These plans include:
- Sending a spacecraft to land on the asteroid and blow it up.
- Impulsive berthing, where a spacecraft would suddenly fly to within inches of an asteroid and slowly push it off course.
- Magnetic sails, which are placed in front of a spacecraft and reflect sunlight onto the asteroid. The sunlight heats the asteroid and boils off some of the small dust particles surrounding it, pushing the main body of the asteroid off

</details>

> ### Tortoise’s Global AI Index shifts narrative

<details>
  <summary>Read output</summary>

**Tortoise’s Global AI Index shifts narrative.** When the international affairs think tank Tortoise published its AI index last year, there was little reason to suppose it would become one of the most influential new assessments of global progress. But instead, the Global AI Index – or Gaxi for short – quickly became the Rosetta Stone for how to make sense of a staggeringly complex transition from human to digital intelligence.

“We thought we would be useful for ministers and heads of international organisations for whom we could summarise complex information about their countries in a simple ranking,” Tortoise’s founder and executive chairman, Francis Gurtraff, tells Tortoise Weekly.

A year on, Tortoise’s Gaxi report is one of the fastest rising publications in history (#536, according to statistics website Semantic GM).

For context, 7 million books were published between 2010 and 2019. The most popular of all time – The Lord of the Rings – sold 250 million copies.

In that same period, more than 35,000 research papers and doctoral theses were published in China alone.

It's no surprise then that Gaxi has upended the global conversation about whether smart machines deliver progress by looking at what actually happens to people when smart systems are deployed in their lives. In other words: correlation, not causation.

The index provides a measure of how AI serves top-down (government) or bottom-up (business) goals at the national level and highlights
- individual, developmental and cognitive impacts;
- multi- and trans-sectoral linkages between AI and human decision-making;
- capacity for strategies to adapt to change; and
 “moral” risks of entrusting decisions to machines (most notably, data bias and human jobs where human oversight is not possible).

The Gaxi formula works. Low scores correlate strongly with real-world problems, as Tortoise has found in subsequent research. Read on for more detail

</details>

## Notes
- Fine-tuning an OpenAI model isn't free: 300 prompt-completion pairs (200-300 tokens ea.) cost me ~$20. If cost is a limiting factor you can train on cheaper models - [pricing info](https://openai.com/api/pricing/)
- This project, (and the OpenAI API) expect the API key to be saved as the environment variable `OPENAI_API_KEY`.
