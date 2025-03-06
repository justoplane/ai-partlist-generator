# AI Part Shopping Helper
This app will take a user description of a project they want to build and then generate both a list of parts and tools that will be needed, but will also store all generated content in a database. The app will then, upon request, generate links to purchase said list items online.

## Get AI list and parse results
- Submit request to AI and wait for response
- Parse AI result, looking for numbers.
- Put results in database and populate on page

## Project Structure
### Main Page
- Consists of a list of previous prompts, showing the prompt and a link to the result page.
- A button spans the bottom of the screen, allowing the user to start a new prompt.
  - When user selects the button, the list will collapse to a smaller size, and the button will expand into a text entry box. 
  - Submitting the form of the text entry box will swap the user to the corresponding results page.
### Results Page
- A heading at the top of the page gives the name of the project and its description.
- A table below that shows each item required for the project, its quantity

### Sample Prompt and output
I will give you an example input, an example output, and then the input that you should respond to, following the pattern set by the example given.

Example Input:
Give me a list of tools and materials that I would need to build a table. It is described as an 8 foot long by 4 foot wide dining room table, made of oak hardwood. When you generate the list, include your best estimation of the required quantity of each item, as well as a cost estimation for each item. Make sure that each list item consists of only one purchasable product. Your response should be generated as JSON data, including only the fields, "name", "quantity", and "estimated_cost", with no extraneous descriptions.

Example Output:
[
  {
    "name": "Oak Hardwood Boards",
    "quantity": "Approximately 30 board feet",
    "estimated_cost": 300
  },
  {
    "name": "Wood Glue",
    "quantity": "1 bottle (16 oz)",
    "estimated_cost": 5
  },
  {
    "name": "Pocket Hole Screws",
    "quantity": "1 box (100 count, 2.5-inch length)",
    "estimated_cost": 10
  },
  {
    "name": "Sandpaper Assortment Pack",
    "quantity": "1 pack (various grits)",
    "estimated_cost": 15
  },
  {
    "name": "Wood Stain",
    "quantity": "1 quart",
    "estimated_cost": 10
  },
  {
    "name": "Polyurethane Finish",
    "quantity": "1 quart",
    "estimated_cost": 15
  },
  {
    "name": "Clamps",
    "quantity": "4 bar clamps (24-inch)",
    "estimated_cost": 80
  },
  {
    "name": "Miter Saw",
    "quantity": "1 unit",
    "estimated_cost": 200
  },
  {
    "name": "Table Saw",
    "quantity": "1 unit",
    "estimated_cost": 300
  },
  {
    "name": "Drill",
    "quantity": "1 unit",
    "estimated_cost": 50
  },
  {
    "name": "Pocket Hole Jig",
    "quantity": "1 unit",
    "estimated_cost": 40
  },
  {
    "name": "Orbital Sander",
    "quantity": "1 unit",
    "estimated_cost": 60
  },
  {
    "name": "Measuring Tape",
    "quantity": "1 unit (25-foot)",
    "estimated_cost": 10
  },
  {
    "name": "Safety Glasses",
    "quantity": "1 pair",
    "estimated_cost": 5
  },
  {
    "name": "Hearing Protection",
    "quantity": "1 pair",
    "estimated_cost": 15
  },
  {
    "name": "Dust Mask",
    "quantity": "1 pack (5 masks)",
    "estimated_cost": 10
  },
  {
    "name": "Wood Chisels",
    "quantity": "1 set (4 pieces)",
    "estimated_cost": 30
  },
  {
    "name": "Mallet",
    "quantity": "1 unit",
    "estimated_cost": 15
  },
  {
    "name": "Router",
    "quantity": "1 unit",
    "estimated_cost": 100
  },
  {
    "name": "Router Bits Set",
    "quantity": "1 set (10 pieces)",
    "estimated_cost": 50
  },
  {
    "name": "Circular Saw",
    "quantity": "1 unit",
    "estimated_cost": 100
  },
  {
    "name": "Workbenches",
    "quantity": "2 units",
    "estimated_cost": 200
  },
  {
    "name": "Wood Filler",
    "quantity": "1 container (16 oz)",
    "estimated_cost": 10
  },
  {
    "name": "Screws Assortment Pack",
    "quantity": "1 pack (various sizes)",
    "estimated_cost": 20
  },
  {
    "name": "Wood Conditioner",
    "quantity": "1 quart",
    "estimated_cost": 15
  }
]

True Input:
Give me a list of tools and materials that I would need to build a cabinet. It is described as a freestanding birch cabinet, with inner dimensions of 36" tall, 16" wide, and 20" deep. When you generate the list, include your best estimation of the required quantity of each item, as well as a cost estimation for each item. Make sure that each list item consists of only one purchasable product. Your response should be generated as JSON data, including only the fields, "name", "quantity", and "estimated_cost", with no extraneous descriptions.