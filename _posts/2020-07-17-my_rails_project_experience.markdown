---
layout: post
title:      "My Rails Project Experience"
date:       2020-07-17 13:52:44 -0400
permalink:  my_rails_project_experience
---


My rails application doesn't exactly look the greatest but I can now proudly say I’ve finally built my first rails application from SCRATCH! This project was quite challenging, and I did spend a myriad of hours debugging but I learned a lot out of it and the feeling after fixing a bug is absolutely satisfying. Even when I have no idea why my code works but it works!

![](https://i.imgur.com/Cb426qO.gif)

Like many, I had a lot of ups and down doing this rails project & one of the few issues I came across was with my review’s create form. My form is nested with a total of three different models which was the restaurant, location & review. Saving & Creating the new instance for a review was fine but the biggest issue I had was trying to create the nested objects. I updated my strong paramenters in the review’s controller & even used “accepts_nested_attributes_for” method in my review model class but it still was not working. After long hours and with the help of my cohort coach, I realized I had to add these lines to the create method located in review’s controller for both @restaurant & @location. By doing this, it would be able to create the nested objects or return the found objects.

```
def create 
        @review = Review.new(review_params)
        @location = Location.find_or_create_by(city: params[:review][:location][:city], country: params[:review][:location][:country])
        @restaurant = Restaurant.find_or_create_by(name: params[:review][:restaurant][:name], location_id: @location.id)
        @review.user_id = session[:user_id]
        @review.location_id = @location.id
        @review.restaurant_id = @restaurant.id
```
				
Luckily, that did the trick and displayed all the nested attributes wonderfully in my HTML files. 

![](https://i.imgur.com/4ZNRH0W.gif)


However, one of the things I enjoyed most about Ruby on Rails is the generator commands they offer. It saved me so much time from having to manually create files/folders/migrations which I found extremely helpful. If I were to make a mistake in my migrations and of course, I always do, it can be undone with just a simple command in the terminal. 

```
rails generate migration table_name 
rails d migration table_name
rails generate model 
rails generate controller ...etc 
```
Overall, I’ve really enjoyed building this rails project. It was intimidating at first but once everything pulled together into a website, it was truly astonishing and inspiring.


