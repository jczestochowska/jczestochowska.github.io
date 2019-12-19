
**With more than 14'000 restaurants, food is a serious business in Chicago. But choosing where to eat is not an easy task, especially when you want to avoid risky places. Our choices are usually affected by the reviews of other visitors and the location of the restaurant. But do we ever wonder if a restaurant fulfils all sanitary standards?**

Using [Chicago Food Inspection data](https://www.kaggle.com/chicago/chicago-food-inspections), our goal is to provide insights into food quality in the Windy City. We want to explore what are the violations that restaurants make most often, how they change over time and are they connected to the area where restaurant is located.

Let's imagine that you are going to Chicago next week. It can be a business trip or a leisure, whichever you prefer in the moment. You'll be staying in Chicago for four days and you would want to explore the local gastronomy. A morning coffee with a lake view, then lunch with an old friend in one of local's hidden gem places and, in the end of the day a nice, romantic dinner with a glass of white vine. Perfect day is easy to imagine, but hard to implement, right? If you want perfect meals for any part of the day, you have to spend some time figuring out which places you want to visit in an unknown city. 

So, what would be your approach to find a good restaurant? For sure Google will be your friend in this exploration. Nowadays, we rarely visit places without checking the user reviews on TripAdvisor and Facebook, and we always look at the magnificent pictures of food that restaurants publish on their Instagram profiles. Also, we always know someone who knows someone who has recently been in Chicago, so we don't hesitate to contact them and ask for some reccomendations. 

Okay, those are pretty much standard approaches. Any other thoughts? 

What if we tell you that we looked at restaurant's inspection results to figure out where to eat in Chicago? That's it, thousands of inspection reports with notes of poor inspectors saying that they saw cockroach in the pantry or closed the restaurants because they lacked defined vomiting procedures. We guess that, when going to a restaurant, you rarely think if it fullfils all standards issued by the city. We believed that, using inspection results and non-standard approach to the "where-to-eat-tonight" problem, we can assess which restaurant is worth visiting. 

The dataset we used contains information from inspections of restaurants and other food establishments in Chicago in the past ten years.

<div id="bigger_wrapper">
    <div id="map_wrapper">
        <div id="lqi_map">
            {% include lqi_map.html %}
        </div>
        <div id="map_text">
            <p>I'm on the second on the left</p>
        </div>
    </div>
    <div>
        {% include results_of_inspections_per_year.html %}
    <div/>
</div>

<div>
{% include sd_critical_district.html %}
<div>

<div>
{% include sd_critical_community.html %}
<div>

<div>
{% include sd_failed_district.html %}
<div>

<div>
{% include sd_failed_community.html %}
<div>

<div>
{% include sd_refailed_district.html %}
<div>

<div>
{% include sd_refailed_community.html %}
<div>

<div>
{% include sd_complaints_district.html %}
<div>

<div>
{% include sd_complaints_community.html %}
<div>
