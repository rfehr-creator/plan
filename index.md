# Sorting Plan
I see the sorting problem in 2 major parts. 
- The first part is creating the actual sorting, which likely will be just a docker image.
- Then the second part would be integrating part 1 into the existing system. 

## Part 1
The idea would be that this API would receive a single pdf file and return a json object containing all the information needed to create one or more documents. The detailed steps are:
- Determine the vendor for each page
- Get the page number for each page
- Use the vendor and page number for each page to create one or more documents
  - Extract the Date (Bill date or Statement Date)
  - Extract the Amount (For bills only)

## Part 2
