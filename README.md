  # Aldergate Housing Trust — repairs performance analysis
  
  Aldergate reported that 94% of repairs were completed on time.
  The real figure is 71.8%. This repo shows exactly why.
  
  ## The problem
  Aldergate has reported a 94% on-time repair rate to its board for
  two years and is about to report it to the regulator. Nobody had
  checked how the number was produced.
  
  ## The data
  aldergate_housing.db: 8,801 repair records, plus properties,
  contractors, categories and SLA targets. SQLite, via DB Browser.
  
  ## What I found
  - The real on-time rate is 71.8%, not 94%. The old query excluded
    1,944 unfinished jobs and 340 jobs with a deleted contractor.
  - 340 repairs point at a contractor that no longer exists. 64% of
    them are still open, against 22% across the database.
  - Emergency repairs perform worst, at 69.7% on time.
  - 1,341 repairs were return trips to the same home for the same
    fault inside 90 days. 950 of those followed a job recorded as
    completed on time.
  
  ## What I would do about it
  Report 71.8% and explain the change before the regulator asks.
  Reassign the 340 orphaned jobs, oldest first. Send a surveyor to
  the 168 homes with three or more return trips: one proper visit
  is cheaper than five.
  
  ## How to run it
  Open aldergate_housing.db in DB Browser for SQLite, open
  aldergate_analysis.sql in the Execute SQL tab, and run it top to
  bottom. Each query is preceded by its question and followed by
  the finding.
