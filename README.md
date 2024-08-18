# Fine tuning T5 Large для генерации шуток, в стиле вопрос - ответ.
## Описание задачи.
Есть датасэт скаченных шуток из reddit/jokes в стиле вопрос ответ, например - 
> What animal has more lives than a cat? A frog. It croaks every night.

В качетсве модели была выбрана pre-trained [T5 Large](https://huggingface.co/google/flan-t5-large).
Для начала нужно понять какой уровень может предоставить модель без дообучения. Так же для наглядности приведу ответы полученые с помощью [Gemini](https://gemini.google.com/)

Шутка | Original | T5 | Gemini 
--- | --- | --- | ---
What do The Sixth Sense and Titanic have in common? | Icy Dead People. | they are both about a woman | They both have terrible endings.
If Hillary Clinton and Donald Drumpf are in a boat and it capsizes. Who survives? | America | Donald Drumpf |  I can't help with responses on elections and political figures right now.
Why do Yoda's jokes always suck? | Says the punch line first, he does | Yoda is a snob | Because they're so old, they're always punchlines.
What do you call a little Mexican? | A paragraph. Because he's not quite an essay | a little samoan | A mini-taco.
Did you hear that Jared from Subway was caught up in a child pornography investigation? | Brings a whole new meaning to their slogan, "Eat Fresh." | Jared from Subway was caught up in a child pornography investigation | I'm unable to provide an answer to that question.
Do you know what Twitter is?| It's the spot between your twat and shitter. | Twitter is a social networking site | It's a digital birdcage where people share their thoughts for the world to see. Or as some call it, a never-ending soap opera with way too many opinions.
How many developers does it take to change a light bulb? | None. That's a hardware problem. | a light bulb is a light bulb | None. That's a hardware problem.
What's the speed limit of sex? | 68 Because at 69, you flip over and eat it. | sex is a speed limit of 100 mph | Sixty-eight. At sixty-nine you have to turn around.

Как можно заметить Т5 не сарвляется с задачей. Gemini отвечает нанмого лучше, однако из-за фильтрации контента, не может ответить на ряд шуток.

## Оценка качества.
Прежде чем заниматься моделью нужно определиться как собственно оценивать качество полученного результата? Проблематки здесь в том, что выбор метрики качества для такого рода задач не является тривиальным, так как юмор — субъективное понятие. И в идельных условях, нужна человечская разметка на *Рейтинг смешности* и *Рейтинг уместности*. Приедтся ориентироваться, на полученные результаты по примерам.
