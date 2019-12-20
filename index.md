<!---
**With more than 14'000 restaurants, food is a serious business in Chicago. But choosing where to eat is not an easy task, especially when you want to avoid risky places. Our choices are usually affected by the reviews of other visitors and the location of the restaurant. But do we ever wonder if a restaurant fulfils all sanitary standards?**

Using [Chicago Food Inspection data](https://www.kaggle.com/chicago/chicago-food-inspections), our goal is to provide insights into food quality in the Windy City. We want to explore what are the violations that restaurants make most often, how they change over time and are they connected to the area where restaurant is located.
--->
Imagine that you are traveling to Chicago next week. Should it be for business or leisure, you'll be staying in Chicago for four days and you would like to discover the local gastronomy. A morning coffee with a lake view, then lunch with an old friend in a local hidden gem place and, in the end of the day a nice, romantic dinner. 

But imagination is not enough to make such a perfect day happen ! If you want perfect meals for any part of the day, you have to spend some time figuring out which places you want to visit. This can often be a challenging and frustrating task, especially in an unknown city. 

So, what would be your approach to find a good restaurant? For sure, Google will be your friend in this exploration. Nowadays, few people visit places without checking user reviews on TripAdvisor and Facebook, and the magnificent pictures of food that restaurants publish on their Instagram profiles are often used as selection criteria. And let's not forget friends of friends of friends who have recently been in Chicago, who can often offer usefult recommendations.

Okay, those are pretty much standard approaches. Why not try something different? 

What if we tell you that we looked at restaurant's inspection results to figure out where to eat in Chicago? That's right, thousands of inspection reports with notes of poor inspectors relating their encounters with cockroaches in pantries, or that they closed restaurants because they lacked defined vomiting procedures. When going to a restaurant, you rarely wonder if it fullfils all standards issued by the authorities. However, inspection results can be used as a non-standard approach to the "where-to-eat-tonight" problem, and are very useful to assess which restaurants in the Windy City are worth visiting. 

The dataset we used contains information from inspections of restaurants and other food establishments in Chicago in the past ten years. Every inspection comes with basic information about the restaurant such as name, licence number, location, zip code, then the type of the inspection that was performed and, of course, the result of the inspection followed by a description of the violations discovered.

Let's start with a quick look on the inspection results of the past ten years.

{% include results_of_inspections_per_year.html %}

It seems that majority of the restaurants managed to pass their inspections before 2018 but afterwards we can see increase in inspections that passed with conditions. What may have caused that? It is clearly not enough to look just at pass and fail we would like to discover what are the reasons behind inspection failure.

#### Violations

So, if we really want to figure out how good a restaurant is, based on the inspection results, the common sence tells us that if a restaurant makes many violations, we might reconsider our decision to visit it. That is why we wanted to check how many violations restaurants make on average per inspection. But looking at several thousand of restaurants at a time isn't really possible, so we first group all of the restaurants based on their location. The city of Chicago is officially divided into 77 community areas, which are grouped into 9 districts. We used this geographical and administrative partition of the city as a starting point and checked how many violations per inspection restaurants make on average in each community area. **TODO**: Comment

**INSERT** Map of average number of violations per inspection per area

Now one knows the numbers, but there is still a mystery what hides behind them. Observed violations can differ in the aspect of the restaurant their describe: there can be some issues with the food, with the facilities or the training of the personnel. Knowing which violations and where were the most prevalent could give us some understanding. Was it related to food preparation process or cleaningness of the toilets? We can also find this kind of information.

**One note before we start:** Chicago changed their violation definitions in the middle of 2018. Before the change an establishment could receive one or more of 45 distinct violations. After the change, the violations were redefined and their number increased to 59. Also, the inspections became much stricter and now restaurant is more likely to rather get just a "Pass with conditions" than a clear "Pass" if it violates some criteria. That is why we will usually look at those two periods separately.

Although every violation describes some specific shortcoming of a restaurant, all of them, both before and after the change, can be grouped into 5 general categories:

1. **Food violations:** violations that are related to the food and ingredients: the way they are obtained, stored, transported, prepared, labeled etc.
2. **Facility conditions violations:** presence of appropriatelly set up equipment and utilities (freezer, owens, work surface etc.), as well as requirements for the building and infrastructure (lighting, ventilation, temperature, pipes, walls etc.).
3. **Sanitary related violations:** violations that are related to keeping all the equipment, rooms and surfaces clean .
4. **Staff related violations:** violations related to the employees (necesarry trainings, the way they work with food, manager's work etc.).
5. **Other:** the violations that did not match the previous groups (eg. summary report of the inspection visible to the public, no smoking regulations etc.).

Now, being familiar with that, let's dive into the analysis!

First let's if there are any patterns of the most common violations noted in Chicago. As mentioned, we can look at Chicago before the change of violations and after it.

<div id="bigger_wrapper">
    <div class="clearfix" id="map_wrapper">
        <div class="map-400 map-left">
            {% include most_common_violations_before_change.html %}
        </div>
        <div id="map_text">
            <p>Before the July of 2018 the predominant violation in most Chicago communities is **Proper floors maintenance**. Between Cicero and Oak Loan in the south-west side of Chicago you can also find the region of 7 communities, for whose restaurants the *Clean equipment* criterion was violated the most</p>
        </div>
    </div>
</div>

<div id="bigger_wrapper">
    <div class="clearfix" id="map_wrapper">
        <div class="map-600 map-right">
            {% include most_common_violations_after_change.html %}
        </div>
        <div id="map_text">
            <p>After the change of violations restaurants in the huge part of the middle and southern bay area as well as the region between the New City and Greater Grand Crossing most oftenly violated **Adequate management** criterion - this concerns regulations about personell hierarchy and their reporting procuders. There are also regions in the north south and west of Chicago	where *Procedures for reacting to customer sickness* was the most common issue.</p>
        </div>
    </div>
</div>

<!-- Number of inspections tells us how many different fouls restaurant made, but it doesn't give any information about the core of the violation. Was it some life-threathening violation, or hazardous one? -->

Since our goal is to filter bad restaurants, let's now focus only on the violations which were noticed in inspections that ended with failure. In the plot you can see the 25 most common violations in failed inspections before the violation change.

{% include violations_failed_category_before_change.html %}

We have a winner! As it was also seen on community maps of all violations, also among the failed inspections only, dirty floor was mentioned the most as one of the violations. Two out of top three violations are related to cleaningness in the restaurant. Interestingly, many restaurants have problems with walls and ceiling constructions. Of course, there could be that some part of ceiling and wall problems is also due to dirtiness apart from construction.

It seems that "most popular violations" are sanitary and facility related. It is surprising that even though we are analysing restaurants, there is only one food related violation among the top 10 and it is on 10th place.

Even though after June 2018. violations changed, since we group violations in the same 5 categories as before, let's check if there is any change in the most frequent violation categories in failed inspections.

{% include violations_failed_category_after_change.html %}

We already mentioned the big differences and stricter criteria after the change date. That can also be noticed in the most often violations. Now for the first time we can see a big impact of **violations related to employees training**. Apparently, many restaurants did not have time do adjust properly to the new regulations and failed in the past year and a half due to inadequate management or lack of allergen training for the staff. Also, the City of Chicago requires defined procedures for many situations that can happen in a restaurant, and one that is the most problematic for restaurants to comply with is **reacting in case of customer sickness.** So be careful and remind yourself of your first aid knowledge, because the restaurant employees apparently cannot help you properly. Of course, when looking at these reasons, we have to take into account that these changed violation list is valid for less than 18 months, so there is a smaller amount of inspections which can be analyzed.

Great, now we had a deeper look into the meaning of the violations and understood what are the main problems for the restaurant. However, we still haven't considered the severity of the discovered violations. Validations before change were divided into 3 groups based on how serious the violation is: critical, serious or minor violation, sorted in decreasing severity.

Of course the main interest point for us are critical violations. Those are the most serious and dangerous violations a restaurant can make. Therefore, we want to see what are the most frequent critical violations in inspections.

{% include violations_failed_critical_category_before_change.html %}

If based on previous plots we wondered where are the food related violations in restaurants' inspections, here they are. When looking at critical violations only, the top violation is related to **proper food storage temperature**. According to the full violation description, it means that potentially hazardous food meets temperature requirements during storage, preparation and service. On second and third place we have facility related violations, and then come the ones related to adequate cleaning of all necessary areas and equipement.

<div id="bigger_wrapper">
    <div id="map_wrapper">
        <div id="lqi_map">
            {% include lqi_map.html %}
        </div>
        <div id="map_text">
            <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.

Why do we use it?
It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).
</p>
        </div>
    </div>
</div>



#### Safe and Dangerous Areas to Eat


Now that we have discovered what are the violations restaurants make, let's use these insights to get some recommendations which places should be favored, and which ones avoided. Our idea is to use area in which the restaurant is located and try to discover which community areas are the safest ones considering the inspections' results. 



As we previously discussed, not all violations are the same, and the most severe ones are critical violations. Therefore, if there are many inspections in which they were discovered, the area is considered more dangerous.

**TODO**: Change with single plot

<div>
{% include sd_critical_district.html %}
</div>

<div>
{% include sd_critical_community.html %}
</div>

By looking at districts, we can see that South Side restaurants make the most critical violations, where Northwest side is the safest district considering this criteria. If we take a closer look, Washington park restaurants on average make critical violation every fourth inspection. Oakland in South Side and Uptown in Far North Side are also highly ranked and can get a title of dangerous areas. 



Another criteria we can use is number of inspections ended in failure. Naturally, if there are more failures, the area is more dangerous. We will check the proportion of failures among total inspections for each area. If it is higher for some areas then for others, we consider them more dangerous areas.

<div>
{% include sd_failed_district.html %}
</div>

<div>
{% include sd_failed_community.html %}
</div>

Again, South Side is the district to avoid. Interestingly, city center has the lowest percentage of failed inspections. As the critical areas, we again have Oakland and Washington park as leading restaurant-dangerous communities in Chicago.



Even though we are now focused on choosing the place to eat based on formal criteria like inspections, we would still like to include some user's opinion. Among all the inspections, there are some inspections of type complaint and suspected food poisoning. Complaint type means that the inspection is done inresponse to a complaint against the establishment. Suspected food poisioning is a specific type of complaint based inspection, when the inspection is done in response to one or more persons claiming to have gotten ill as a result of eating at the establishment. Therefore we will check number of inspections of type Complaint or Suspected Food Poisoning, because these inspections imply that users haven't been satisfied with the conditions in the restaurants. 

<div>
{% include sd_complaints_district.html %}
</div>

<div>
{% include sd_complaints_community.html %}
</div>

We can clearly see that South is deffinitely more problematic than North. Chatham and Calumet Heights have on average around 3.5 complaints per restaurant. What is really interesting that Oakland, previously considered as food-dangerous area, didn't have any complaint inspection in the previous ten years! Apparently users do not notice the problems that ispectors continuously find in the Oakland restaurants.

**TODO** : Safety score map

<div>
{% include safety_scores_by_community_areas_map.html %}
</div>
