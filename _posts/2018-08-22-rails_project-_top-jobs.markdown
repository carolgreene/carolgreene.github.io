---
layout: post
title:      "Rails Project- Top-Jobs"
date:       2018-08-22 21:52:19 +0000
permalink:  rails_project-_top-jobs
---


I am so glad to finally finish my Rails Project. This one was definitely a lot  more complicated than the other projects and took waaaay longer to finish than I thought it would. I ran into several issues that slowed me down starting with the fact that I was still using the IDE. I was not able to even create a new rails app in the IDE and had to switch to a local environment by installing Virtual Box since I have a Windows computer.  Once I finally got that up & running I had to chart out my project. 
I decided to do a Job Search site since I figured that  I'm going to be doing a lot of job searching in the near future. I struggled over how to handle my users, whether to have separate models for applicants & companies and finally decided to use ENUM roles within the User class.  I ended up with the following models & relationships:

```
class User < ApplicationRecord
enum role: [:applicant, :company] 

    has_many :jobs, :foreign_key => 'company_id', source: :company

    has_many :job_applications, :foreign_key => 'user_id'
    has_many :applied_jobs, through: :job_applications, :class_name => 'Job', :foreign_key => 'applicant_id', source: :applicant
```

```
class Job < ApplicationRecord
belongs_to :company, :class_name => 'User', :foreign_key => 'company_id'
    has_many :job_applications 
    has_many :applicants, :through => :job_applications, :class_name => 'User', :foreign_key => 'applicant_id' 
```

```
class JobApplication < ApplicationRecord
belongs_to :job 
    belongs_to :applicant, :class_name => 'User', :foreign_key => 'applicant_id' 
```
I liked this set up because it was straight forward and seemed to operate in a logical manner.  I didn't want to make the app too complicated. As it was, I felt like I had to dial it back quite often so I wouldn't lose control of it.

I decided to do my own validations, making sure to validate the presence of each field for  my forms. I also made sure to validate the uniqueness of the user's name so I wouldn't have duplicates.  

I wrote the basic methods for the controller and had it up & running pretty quickly. Basically, anyone can view the job list, but would need to sign in for anything else.  Companies can post new jobs and see a list of applicants that have applied to each of their postings. They can click on the applicant to see the actual application.  They can also edit & delete their job listings. Applicants can click on jobs and apply to them. They can also see a list of the jobs they've applied to. They can edit & delete their applications, which we know can't be done in real life, but I wanted to show it anyway. 

I decided to use the Pundit gem for my Authorization and really liked it. It keeps the code in a separate policy class for each model. I've listed the JobPolicy class below.
```
class JobPolicy < ApplicationPolicy 

   def created_by_company?
     user.company? && record.company_id == user.id 
   end 

   def new?
    user.company?
   end

   def create?
    user.company?
   end 

   def update?
    created_by_company? 
   end 

   def destroy?
    created_by_company?
   end
end

```
Then in the controller all I had to do was authorize @job. There were some things about Pundit I didn't quite understand, but I was able to do what I needed to do.

The last thing I did was set up OAuth for Facebook. I was glad I waited until everything else was working because I ran into some issues with that also. Avi's lecture on OAuth was extremely helpful & I was really happy once it all worked!

All in all, I really liked doing this project and can't believe how much I've learned. Rails can be really complicated and I struggled with understanding it.  My project helped me get a much better feel for it, and I can see a lot of different things I can change in the future to make it better.

