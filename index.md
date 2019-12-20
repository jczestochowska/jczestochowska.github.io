<!---
**With more than 14'000 restaurants, food is a serious business in Chicago. But choosing where to eat is not an easy task, especially when you want to avoid risky places. Our choices are usually affected by the reviews of other visitors and the location of the restaurant. But do we ever wonder if a restaurant fulfils all sanitary standards?**

Using [Chicago Food Inspection data](https://www.kaggle.com/chicago/chicago-food-inspections), our goal is to provide insights into food quality in the Windy City. We want to explore what are the violations that restaurants make most often, how they change over time and are they connected to the area where restaurant is located.
--->
Imagine that you are going to Chicago next week. It can be a business trip or a leisure, whichever you prefer in the moment. You'll be staying in Chicago for four days and you would want to explore the local gastronomy. A morning coffee with a lake view, then lunch with an old friend in one of local's hidden gem places and, in the end of the day a nice, romantic dinner with a glass of white vine. 

Perfect day is easy to imagine, but hard to implement, right? If you want perfect meals for any part of the day, you have to spend some time figuring out which places you want to visit. This can often be a challenging and frustrating task, especially if you are in an unknown city. 

So, what would be your approach to find a good restaurant? For sure Google will be your friend in this exploration. Nowadays, we rarely visit places without checking the user reviews on TripAdvisor and Facebook, and we always look at the magnificent pictures of food that restaurants publish on their Instagram profiles. Also, we often know someone who knows someone who has recently been in Chicago, so we don't hesitate to contact them and ask for some recommendations. 

Okay, those are pretty much standard approaches. Any other thoughts? 

What if we tell you that we looked at restaurant's inspection results to figure out where to eat in Chicago? That's right, thousands of inspection reports with notes of poor inspectors saying that they saw cockroach in the pantry or that they closed the restaurant because it lacked defined vomiting procedures. When going to a restaurant, you rarely think if it fullfils all standards issued by the authorities. However, we believed that by using inspection results and non-standard approach to the "where-to-eat-tonight" problem, we can assess which restaurants in the Windy City are worth visiting. 

The dataset we used contains information from inspections of restaurants and other food establishments in Chicago in the past ten years. For every inspection, we can see the basic information about the restaurant such as name, licence number, location, Zip code, then the type of the inspection that was performed and, of course, the result of the inspection followed by the description of violations which were discovered.

On the following graph we can see how the inspection results looked like in the past ten years. **TODO**: Comment

**INSERT** Plot Inspection results each year

#### Violations

So, if we really want to figure out how good is the restaurant based on the inspection scores, the common sence tells us that if a restaurant makes many violations, we might reconsider our decision to visit it. That is why we wanted to check how many violations restaurants make on average per inspection. But looking at several thousand of restaurants at a time isn't really possible, so we first group all of the restaurants based on their location. The city of Chicago is officially divided into 77 community areas, which are grouped into 9 districts. We used this geographical and administrative partition of the city as a starting point and checked how many violations per inspection restaurants make on average in each community area. **TODO**: Comment

**INSERT** Map of average number of violations per inspection per area

Number of inspections tells us how many different fouls restaurant made, but it doesn't give any information about the core of the violation. Was it some life-threathening violation, or hazardous one? Was it related to food preparation process or cleaningness of the toilets? We can also find this kind of information. 

Before 1.7.2018., an establishment could receive one or more of 45 distinct violations. After this date, the violations were completely redefined and their number increased to 59. Also, the inspections became much stricter and the result Pass with conditions is the dominant one in the previous year. That is why in the analysis we will usually look at those two periods separately. 

Although every violation desribes specific foult a restaurant can make, all of the violations can be grouped into 5 general categories:

1. **Food violations:** violations that are related to the food and ingredients: the way they are obtained, stored, transported, prepared, labeled etc.
2. **Facility conditions violations:** presence of appropriatelly set up equipment and utilities (freezer, owens, work surface etc.), as well as requirements for the building and infrastructure (lighting, ventilation, temperature, pipes, walls etc.).
3. **Sanitary related violations:** violations that are related to keeping all the equipment, rooms and surfaces clean .
4. **Staff related violations:** violations related to the employees (necesarry trainings, the way they work with food, manager's work etc.).
5. **Other:** the violations that did not match the previous groups (eg. summary report of the inspection visible to the public, no smoking regulations etc.).

Now, let's see what are the violations that are made the most frequently. However, since our goal is to filter bad restaurants, we will focus only on the violations which were noticed in inspections that ended with failure. In the plot we will show top 25 most common violations in failed inspections before 1.7.2018.

{% include violations_failed_category_before_change.html %}

We have a winner! Among the failed inspections, dirty floor was mentioned the most as one of the violations. Two out of top three violations are related to cleaningness in the restaurant. Interestingly, many restaurants have problems with walls and ceiling constructions. Of course, there could be that some part of ceiling and wall problems is also due to dirtiness apart from construction.

It seems that "most popular violations" are sanitary and facility related. What suprises is that, even though we are analysing restaurants, there is only one food related violation among the top 10 and it is on 10th place.

Even though after June 2018. violations changed, since we group violations in the same 5 categories as before, let's check if there is any change in the most frequent violation categories in failed inspections.

{% include violations_failed_category_after_change.html %}

We already mentioned the big differences and stricter criteria after the change date. That can also be noticed in the violations that are made the most. Now for the first time we can see a big impact of **violations related to employees training**. Apparently, many restaurants did not have time do adjust properly to the new regulations and failed in the past year and a half due to inadequate management or lack of allergen training for the staff. Also, the City of Chicago requires defined procedures for many situations that can happen in a restaurant, and one that is the most problematic for restaurants to comply with is **reacting in case of customer sickness.** So be careful and remind yourself of your first aid knowledge, because the restaurant employees apparently cannot help you properly. Of course, when looking at these reasons, we have to take into account that these changed violation list is valid for less than 18 months, so there is smaller amount of inspections which can be analyzed.

Great, now we had a deeper look into the meaning of the violations and understood what are the main problems for the restaurant. However, we still haven't considered the severity of the discovered violations. Validations before change were divided into 3 groups based on how serious the violation is: critical, serious or minor violation, sorted in decreasing severity.

Of course the main interest point for us are critical violations. Those are the most serious and dangerous violations a restaurant can make. Therefore, we want to se what are the most frequent critical violations in inspections.

{% include violations_failed_critical_category_before_change.html %}

If based on previous plots we wondered where are the food related violations in restaurants' inspections, here they are. When looking at critical violations only, the top violation is related to **proper food storage temperature**. According to the full violation description, it means that potentially hazardous food meets temperature requirements during storage, preparation and service. On second and third place we have facility related violations, and then come the ones related to adequate cleaning of all necessary areas and equipement.

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



#### Safe and Dangerous Areas to Eat


Now that we have discovered what are the violations restaurants make, let's use these insights to get some recommendations which places should be favored, and which ones avoided. Our idea is to use area in which the restaurant is located and try to discover which community areas are the safest ones considering the inspections' results. 



As we previously discussed, not all violations are the same, and the most severe ones are critical violations. Therefore, if there are many inspections in which they were discovered, the area is considered more dangerous.

**TODO**: Change with single plot

<div>
{% include sd_critical_district.html %}
<div>

<div>
{% include sd_critical_community.html %}
<div>

By looking at districts, we can see that South Side restaurants make the most critical violations, where Northwest side is the safest district considering this criteria. If we take a closer look, Washington park restaurants on average make critical violation every fourth inspection. Oakland in South Side and Uptown in Far North Side are also highly ranked and can get a title of dangerous areas. 



Another criteria we can use is number of inspections ended in failure. Naturally, if there are more failures, the area is more dangerous. We will check the proportion of failures among total inspections for each area. If it is higher for some areas then for others, we consider them more dangerous areas.

<div>
{% include sd_failed_district.html %}
<div>

<div>
{% include sd_failed_community.html %}
<div>

Again, South Side is the district to avoid. Interestingly, city center has the lowest percentage of failed inspections. As the critical areas, we again have Oakland and Washington park as leading restaurant-dangerous communities in Chicago.



Even though we are now focused on choosing the place to eat based on formal criteria like inspections, we would still like to include some user's opinion. Among all the inspections, there are some inspections of type complaint and suspected food poisoning. Complaint type means that the inspection is done inresponse to a complaint against the establishment. Suspected food poisioning is a specific type of complaint based inspection, when the inspection is done in response to one or more persons claiming to have gotten ill as a result of eating at the establishment. Therefore we will check number of inspections of type Complaint or Suspected Food Poisoning, because these inspections imply that users haven't been satisfied with the conditions in the restaurants. 

<div>
{% include sd_complaints_district.html %}
<div>

<div>
{% include sd_complaints_community.html %}
<div>

We can clearly see that South is deffinitely more problematic than North. Chatham and Calumet Heights have on average around 3.5 complaints per restaurant. What is really interesting that Oakland, previously considered as food-dangerous area, didn't have any complaint inspection in the previous ten years! Apparently users do not notice the problems that ispectors continuously find in the Oakland restaurants.

**TODO** : Safety score map