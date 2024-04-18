# ixdf-questions
1. **Please describe an interest, favorite activity, or hobby of yours. It could be anything: just something you enjoy doing. For this particular answer, please only write up to 60 words and do it in a way that captivates your readers (us!).**
 
    **>>** I enjoy quiet activities. Reading in a cozy spot is my go-to, along with sewing—it's calming, and I love creating new things, whether it's clothes, recipes, or coding. Walking my dog is another favourite, especially now that she's mastered walking beside me. 

2. **What is most important to you when you look for a new job? Please be completely honest and transparent about your situation and season of life; we’re not looking for “the right answer”. The more you tell us, the better we can align.**

    **>>** In this phase in my life, what I’m looking in a job is collaborative and supportive team, freedom to work from anywhere and possibility to make an impact. I fully engage into my work and company that sees and values my efforts is ideal for me. 

3. **Everyone learns differently. How do you learn best? And what’s something new that you’ve learned in the past few months? Big or small, we’re curious!**

    **>>** Best way for me to learn is through documentation, I find reading about subject more understandable for me. For example If I’m learning something new regarding framework I would prefer to visit their official documentation, if there is something that I can not find there than I’ll try to find some trustworthy articles or videos to watch, after that I try to use learnt subject in an example if it’s possible and  try it out to fully understand it.  

    For example: In last months I got enrolled into the project which needed to be rewritten for performance reasons, client required frontend of the project to be rewritten on Angular, so I needed to look into Angular’s documentation and learn as much as possible of it’s latest version to start project and rewrite it. 

4. **How did you hear about this open position?**

    **>>** I discovered this open position while searching Google for remote PHP Laravel developer roles. I found your listing on the careers page.

5. **Show us some examples of concrete work you’re proud of having done yourself. Please tell us why you are proud of what you sent us. Please be as specific as possible.**

    **>>** Throughout my work experience, I've encountered various challenging projects, but I'll share two examples here:

    1. In an online shop with multiple merchants and users, we faced the task of integrating Microsoft Dynamics Nav for one of the merchants. The provided APIs posed several challenges, including handling large data sets and undocumented endpoints. My main goal was to optimise data fetching while ensuring accurate analysis of the responses. By thoroughly understanding the endpoints and communicating effectively with stakeholders, I was able to implement efficient data filtering and caching, reducing unnecessary calculations and improving performance.
    
    2. In my latest project, I was tasked with rewriting both the API and frontend. One particularly daunting aspect was untangling a massive codebase with over 5000 lines of code in one controller. After dedicating time to understand the logic behind each part of the code, I successfully refactored it, eliminating unnecessary calculations and reducing the controller to just 50 lines of code, 100 lines of code in service and several methods in models for relations. This experience was incredibly rewarding, as it allowed me to transform a cluttered codebase into a clean and organised solution 

6. **Can you give a concrete example of a recent situation where you “took ownership” of a task/project/etc at work and made something truly positive happen? How do you define “taking ownership” of your work?**

    **>>** I would describe “taking ownership” as a taking leadership and commitment to the job I do.

    In my previous role, I was the sole PHP developer in a company that primarily focused on outsourcing developers as well as internal projects, Company has several stacks with big teams so I sow potential that team of PHP could be made and grown too.

    Through hard work and successful project deliveries, we began to receive more requests for PHP projects. With management's support, I led efforts to grow the PHP team from just myself to a team of 10 developers within six months, eventually expanding to 16 team members.

    I took it in my hands to start workshops for my team, because quantity desnot means anything, but quality does, I also took initiative for creating knowledge sharing meetings and structured sources.

    I think this journey, from being a sole developer to leading a team it is good example of me taking ownership of my work. 

7. **What are the key skills you (would) bring to an asynchronous and remote work environment? What key skills do you feel you need to improve for you to fully thrive in such an environment?**

    **>>** During the COVID period, when my company shifted to remote work, I picked up some solid skills that have been a big help in my current fully remote job for the past six months.
These skills include good communication, staying disciplined, managing my time well, and being adaptable. I always start my day by lining my tasks up by priority.
    Self-discipline has always been a thing for me, but it's become even more important with remote work. I stay focused and don't let distractions get in the way—I treat my work hours at home just as seriously as I would in an office.
    Now, building connections with colleagues can be a bit tougher when you're working remotely. I'm kind of in the middle between being introverted and extroverted, but I'm working on getting better at connecting with my coworkers despite the distance.

8. **Which season of life are you currently in and what are your career goals? For example, are you in a season of life where you work long hours to learn as much as possible? Or in a season where you prioritize work-life balance because you’ve already gained substantial experience? The more transparency you give us, the better we can align and create common goals for your career.**

     **>>** I believe that my working experience has been quite adventurous and varied, In this phase of life I would like to balance between work and life, meaning I would be fully engaged in my work but also to have time to be with my family.
 
9. **What is your approach to monitoring the performance of live web applications? What techniques do you use to maintain good performance levels?**

    **>>** Monitoring the performance of live web applications, especially in Laravel, is crucial for ensuring optimal user experience. My aproach is to use:

    1. Real time monitoring tools like New Relic, in larval application sometimes I use pulse on development level.
       
    3. Continues Performance testing, simulating user traffic and checking any slow queries before any deployment to production.
       
    5. I make sure to use cache  for frequently accessed data, which improves response time and overall application performance.
       
    7. Correct logging and error handling is really important, so I make sure to implement logging mechanisms, which later will help to pinpoint problems and bottlenecks.
       
    9. Database optimisation is also crucial, I always implement indexes where it is needed, make sure to add correct constraints. Also one important issue I keep an eye on is N+1 query problem.
  
10. **Could you please send us a sample of some production code you have written and are particularly proud of or find intriguing? Please also explain why you are proud of this code or why you find it interesting**

    **>>** The code snippet I'm providing today is not technically complex and doesn't apply bitwise logic. However, I'm really proud of it because it represents a fragment of the code that replaced a large chunk of the original code while I was rewriting the project, as mentioned in question 5 (example 2). The problem here was undocumented legacy code, which took a long time to declutter. After reinforcing relations and fetching necessary data, I was able to remove unnecessary calculations, loops, and database calls within loops entirely. The main challenge was not writing this code; the main challenge was reducing something massive to this streamlined form. please note that becuase of specific reasons I was not allowed to change anything in tables or names of colomns.

    Fragment from getMonitors funtion
    
        return Monitor::select(
             'idMonitor',
             'label',
             'active',
             'serial',
             'category'
         )
         ->with(['virtualmonitors' => function($query) {
             $query->where('quadrante', 1)->with('strategies');
         }])
         ->whereHas('snaipoint', function ($query) use ($csmfCode) {
             $query->where('csmfCode', '=', $csmfCode);
         })->get();

    Fragment from MonitorController:

        return response()->json(
            Cache::remember(
                CacheKey::MONITORS_LIST->value,
                CacheTime::HALF_HOUR->value,
                fn() => $this->monitorService->getMonitors(Auth::User()->csmfCode)
            )
        );
