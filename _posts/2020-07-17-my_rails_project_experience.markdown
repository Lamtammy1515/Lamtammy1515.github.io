---
layout: post
title:      "My Rails Project Experience"
date:       2020-07-17 13:52:44 -0400
permalink:  my_rails_project_experience
---


My rails application doesn't exactly look the greatest but I can now proudly say I’ve finally built my first rails application from SCRATCH! This project was quite challenging, and I did spend a myriad of hours debugging but I learned a lot out of it and the feeling after fixing a bug is absolutely satisfying. Even when I have no idea why my code works but it works! LOL. 

One of the few issues I came across doing my rails application was with my review’s form. My form is nested with a total of three different tables which was the restaurant, location & review’s table. Saving & Creating the new instance for a review was fine but the biggest issue I had was trying to call the nested attributes in the form to display it in my HTML files. I updated my strong paramenters in the review’s controller & even used “accepts_nested_attributes_for” method in my review model class but it still was not working. After long hours and with the help of my cohort coach, I realized I had to add these lines to the create method located in review’s controller for both @restaurant & @location. That definitely did the trick and worked wonderfully in my HTML files. 


def create 
        @review = Review.new(review_params)
        @location = Location.find_or_create_by(city: params[:review][:location][:city], country: params[:review][:location][:country])
        @restaurant = Restaurant.find_or_create_by(name: params[:review][:restaurant][:name], location_id: @location.id)
        @review.user_id = session[:user_id]
        @review.location_id = @location.id
        @review.restaurant_id = @restaurant.id
				
				
![](https://media0.giphy.com/media/Wsju5zAb5kcOfxJV9i/giphy.gifhttp://)



However, one of the things I enjoyed most about Ruby on Rails is the generator commands they offer. It saved me so much time from having to manually create files/folders/migrations which I found extremely helpful. If I were to make a mistake in my migrations and of course, I always do, it can be undone with just a simple command in the terminal. 

rails generate migration table_name 
rails d migration table_name
rails generate model 
rails generate controller ...etc 

Overall, I’ve really enjoyed building this rails project. It was intimidating at first but once everything pulled together into a website, it was truly astonishing and inspiring.


