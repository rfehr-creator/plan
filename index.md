# Sorting Plan
I see the sorting problem in 2 major parts: 
1. Do the actual sorting.
2. Integrating part 1 into the existing system.

## Part 1
The idea would be to create an API that would receive a single pdf file and return a json object containing all the information needed to create one or more documents. The detailed steps are:
- Determine the vendor for each page
  - Use Tensorflow (Machine Learning) to sort
- Get the page number for each page
  - Options
      - Assume fixed layout (easiest)
      - Use a slightly more dynamic approach to locate a page number
      - Use object detection (likely most time consuming to implement)
          - will work the best across all vendors
- Use the vendor and page number for each page to create one or more documents
  - Extract the Date (Bill date or Statement Date)
    - Options
        - Assume fixed layout (easiest)
        - Use a slightly more dynamic approach to locate the date
        - Use object detection (likely most time consuming to implement)
            - will work the best across all vendors
  - Extract the Amount (For bills only)\
      - Options
        - Assume fixed layout (easiest)
        - Use a slightly more dynamic approach to locate the amount
        - Use object detection (likely most time consuming to implement)
            - will work the best across all vendors

## Part 2
This part would involve integrating Part 1 into the existing as well as determining the architecture for Part 1. Should it be an API or would a Queue be more appropriate?

## My Plan
My plan would be to start small so that it would be farily quick to implement basic sorting from start to finish. I'm thinking of starting with about 20 vendors composed of bank statements and credit cards. This would involve the following steps:
1. Use Tensorflow to train a model to classify those 20 vendors
2. Use a fixed layout approach to extract the page numbers from the page
3. Use a fixed layout approach to extract the date from the first page of the document
4. Use a fixed layout approach to extract the bill amount from the document (if it is a bill)
5. Create an API or Queue
6. Integrate the API or Queue into the main system's workflow
