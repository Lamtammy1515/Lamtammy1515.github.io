---
layout: post
title:      "Rails & Javascript Project 4!"
date:       2020-12-09 16:19:42 -0500
permalink:  rails_and_javascript_project_4
---


Creating this single page application with HTML, JavaScript and CSS for my frontend and Ruby on Rails API as my backend was definitely a new experience. For this project, I made it as simple as it can be to avoid any bugs along the way as my understanding in JavaScript is not the greatest because like many, I am still learning. My simple application basically generates a random meal plan for you across each meal(breakfast, lunch and dinner). I’ve created a function that iterates through each meal stored in my appContainer.js to display three food entrees into the DOM which is triggered whenever you click the button ‘generate meal plan’. Once those three food entrees from each meal displays into the DOM, those entrees will automatically delete from the select options without having to reload the page as this is a single page application. 

One of the few issues I came across was trying to generate three random food entrees from each meal. I got this code off google and I sort of got the functionality that I was looking for but not exactly...

```
let randomFoods = [];
        for (let i = 0; i < 3; i++) {
        randomFoods.push(AppContainer.foods[Math.floor(Math.random()*AppContainer.foods.length)]);
        };
```

This code above however was only able to render three entrees across ALL foods. What I wanted was for it to generate an entree from each meal(breakfast, lunch and dinner). It took some time refactoring but in the end, I was able display what I was targetting into the DOM. Now this code below, located in my appContainer class is what did the trick.

```
let randomFoods = [];
        AppContainer.meals.forEach(meal => {
            randomFoods.push(Food.byMeal(meal.meal)[Math.floor(Math.random()*Food.byMeal(meal.meal).length)])
        });
```


I iterated through the meals stored in appContainer class. For each of those meals(breakfast, lunch & dinner), I'm grabbing an entree from each meal. I also had to build a separate class method called "byMeal" in my food.js file. 


```
  static byMeal(mealMeal) {
      return AppContainer.foods.filter(food => food.meal.meal === mealMeal)
    }
  ```

		
This class method "byMeal" takes in a argument of meal. What this method does is it iterates through the foods stored in appContainer and filters each food entree by its meal based on the meal times. 

Now moving back to this line of code... 

```
randomFoods.push(Food.byMeal(meal.meal)[Math.floor(Math.random()*Food.byMeal(meal.meal).length)])
```

I invoked the class method "byMeal" into this line of code above and I was then able to pull an entree from each meal(breakfast, lunch & dinner). Those entrees were then pushed into the randomFoods array which we are using to instantiate a new mealPlan. 

```
    static generateMealPlan() {
         //generate random foods
         const randomFoods = AppContainer.generateRandomFoods();

        // instantiate a mealplan instance with the random foods
        new MealPlan(randomFoods);
        
        // make fetch request to delete foods from db (IT'S TRIGGERING IT)
        AppAdapter.deleteFoods(randomFoods);
        }
  ```
	
This function above, located inside of the MealPlan class(mealPlan.js file) retrieves the three random entrees from each meal which then instantiates the new random meal plan for us, populates them into the DOM and as well as deleting them from the select options once the meal plan gets displayed.

Overall, this project was definitely new and different in my perspective. I'm just glad I got to experience the ups and downs of this project. I definitely learned a couple of new things from this project about Javascript along the way too. Unfortunately, I did not focus too much on CSS as I was running out of time but it turned out somewhat okay I suppose....



				
				

