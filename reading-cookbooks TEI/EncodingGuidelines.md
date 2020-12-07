# Reading Cookbooks Encoding Guidelines and Workflow

Last updated: 11/30/20 - AMK

---

## Encoding Workflow

1. Transcribe plain text from facsimile images of cookbook 
   
   - We are not encoding line breaks, so they can be ignored in the encoding process. Words hyphenated over lines as a result of line breaks can be treated as their normal, non-hyphenated spellings
   
   - All presentational elements like alignments, all caps, bold, italics, etc will be encoded, they can be ignored in transcription
   
   - Comments for major elements can be added as xml comments `<!-- -->`
   
   - In the shared google doc, areas for further historical research should be highlighted in red and areas with encoding questions should be highlighted in green. Google comments should also be added to note more specific information.

2. Round one of encoding, structural elements
   
   - This round of encoding will be completed by a different person than the person who transcribed the document.
   
   - Each chapter will be contained in it's own XML document.
   
   - Focusing on the major elements of structure such as text divisions, headings, paragraphs, lists, etc.

3. Round two of encoding, contextual elements
   
   - This round of encoding will be completed by a different person than the person who transcribed the document or did the first round of encoding.
   
   - Historical and contextual research is incorporated at this stage
   
   - Focusing on elements like names, notes, interpretations, etc.

4. Correcting and Finalizing encoded documents
   
   - Once all documents for a text are completely encoded a new set of people will check encoding against the current encoding guidelines and the transcription against the facsimile images.

### Getting Started

- File Locations
  
  - Each chapter has its own folder within the folder for the cookbook on the [reading-cookbooks](https://github.com/lizziehop/reading-cookbooks) GitHub

- File Names
  
  - The standardized file name for each chapter will be [cookbook short title][edition-- if relevant] \_ [chap][# in numerical form]
  
  - Example: The Picayune's Creole cook book 4th edition Chapter IV would be PicayuneCookbook4\_chap4.xml 

- Encoding Assistance
  
  - Major encoding questions should be added as an issue to the [reading-cookbooks]([https://github.com/lizziehop/reading-cookbooks](https://github.com/lizziehop/reading-cookbooks/issues) GitHub page and closed when the question has been answered
  
  - Practical encoding questions (ex "how do I...") should be added to the group's internal discussion boards

---

## Encoding Guidelines

*More information coming soon for contextual encoding.*

### Back Matter

- At the same level in the hierarchy as body, this tag surrounds everything at the end of a text such as glossary, acknowledgments, publication information, etc

- ```xml
  <back>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-back.html)

### Body

- The main body of the text, on the same level of the hierarchy as front or back matter and below the text level this contains the whole of the main elements of the document such as chapters 

- ```xml
  <body>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-body.html)

### Chapter Section

- When a chapter is divided into multiple sections, usually by type of dish

- ```xml
  <div type="section"> <!-- the entire section of recipes --> </div>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-div.html)

### Chapter Section Title

- The title for a sigle section in a chapter

- ```xml
  <head rend="align(center) case(allcaps) bold">
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-head.html)

### Chapter Title

- ```xml
  <head rend =“align(center) case(allcaps) bold”>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-head.html)

### Chapter Title - Numerical

- ```xml
  <head rend =“align(center) case(allcaps)”>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-head.html)

### Chapter Title - In French

- ```xml
  <head rend="align(center)"><foreign xml:lang="fr">Le Poisson.</foreign></head>
  ```

- [TEI]([https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-head.html](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-head.html)

### Column Beginning

- Placed at the beginning of a new column with the number attribute as either 1 or 2 depending if it is the first (left) or second (right) column on the page

- This is a self-closing tag, only one needs to be placed where the column beginning happens and the backslash goes at the end

- ```xml
  <cb n=“1”/>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-cb.html)

### Date

- ```xml
  <date when=“mm-dd-yyyy”>
  ```

- Example <date when=“10-31-2020”>On Halloween</date>

- [TEI](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-date.html)

### Foreign Languages

- ```xml
  <foreign xml:lang="<!--two letter language code-->">
  ```

- Example <foreign xml:lang= “fr”>C’est la vie</foreign>

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-foreign.html)

### Front Matter

- At the same level in the hierarchy as body, this tag surrounds everything in the beginning of a text such as publication information, title page, introduction, etc.

- ```xml
  <front>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-front.html)

### Highlight

- For content that is renditionally distinct from other text surrounding it that does not have another tag the `@rend` attribute can be applied to

- Example: an emphasized word in the middle of a paragraph

- ```xml
  <hi rend="<!-add the values for the text's rendition like bold, italic, allcaps, etc. -->">
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-hi.html)

### Ingredient

- Element specific to this project to surround an ingredient in the text

- Ingredients that are pre-made things like broths or syrups should have the xml:id of the recipe as a `corresp` attribute rather than a class

- Adding new type values to the list
  
  - rule of three: if there are three examples of a new type value we add it to the list

- Only tag ingredients in the list 
  
  - Exception is if a new ingredient is mentioned in instructions

- *We are developing another level of attribute specificity for the broad ingredient categories*

- ```xml
  <ingredient xmlns="http://luc.edu/ctsdh/ns/1.0" class="<!--class from closed list-->">
  <!-- OR -->
  <ingredient xmlns="http://luc.edu/ctsdh/ns/1.0" corresp="#pic4.1_fish_soup">
  ```

- Closed List of Values
  
  - meat
  
  - seafood (fish, shellfish, turtles, etc.)
  
  - dairy
  
  - poultry
  
  - egg
  
  - fruit
  
  - vegetable
  
  - herb
  
  - fat
  
  - grain
  
  - leavener
  
  - sugar (refined, cane sugar)
  
  - spice
  
  - slcohol
  
  - extract
  
  - fruit\_juice
  
  - salt
  
  - liquid (vinegar, broth, water, oyster juice, etc. )
  
  - sromatic (garlic, hops, ginger, etc.)
  
  - legume (beans, lentils, peas, peanuts, etc.)
  
  - nut
  
  - condiment
  
  - sweetener (molasses, honey, vanilla sugar, beet sugar, corn sugar, etc. )
  
  - premade 
  
  - pickled (pickles, olives, etc.)
  
  - chocolate
  
  - colorant (carmine powder, etc.)
  
  - undetermined
    
    - Items that do not fit within the current value categories and will be revisited to categorize

### Ingredient Lists

- The entire list is enclosed in a list element with each ingredient in the list as an item, spacing for multiple items on one line etc does not need to be included

- ```xml
  <div type="ingredientList">  
      <list>
          <item><!--a single item in the list--></item>
      </list>
  </div>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/CO.html#COLI)

### Name

- For proper nouns that are not a single person or places 

- Creole or Creoles should be tagged with name, surround the entire noun phrase ie "old creole cook"

- ```xml
  <name>
  ```

- [TEI](https://tei-c.org/release/doc/tei-p5-doc/en/html//ref-name.html)

### Orientation Note

- The preface at the beginning of recipes; after the title and ingredient list, but before the instructions begin

- ```xml
  <div type =“orientationNote”>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-div.html)

### Page Beginning

- Placed at the point where the page begins with the number attribute according to the page number

- This is a self-closing tag, only one needs to be placed where the column beginning happens and the backslash goes at the end

- ```xml
  <pb n="13"/>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-pb.html)

### Paragraphs

- A paragraph in the text, we are not encoding line breaks or words hyphenated over line breaksamk

- ```xml
  <p>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-p.html)

### Place Names

- More information on attributes will be added for round two of encoding

- ```xml
  <placeName>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-placeName.html)

### Personal Names

- More information on attributes will be added for round two of encoding

- ```xml
  <persName>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-persName.html)

### Preface to Chapters

- Introductory material before the first recipe in a chapter

- ```xml
  <div type =“prefatory”>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-div.html)

### Recipe

- Each recipe will have it's own unique xml:id to use as a reference. They will be formatted as [short title of cookbook][chapter number].[recipe number]\_[full title of recipe]
  
  - Example for the first recipe of chapter four, fish soup the xml:id would be pic4.1\_fish\_soup

- ```xml
  <div type =“recipe” xml:id= “pic4.1_fish_soup”>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-div.html)

### Recipe Additions

- the extra information associated with a specific recipe that may have its own title

- Example: “Mock Turtle Eggs” is related to the recipe for "Green Turtle Soup"

- ```xml
  <div type = “recipeAddition” corresp= “#pic4.1_fish_soup”>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-div.html)

### Recipe Instructions

- The instructions within a recipe for how to make the dish

- ```xml
  <div type="instructions">
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-div.html)

### Recipe Title - English

- ```xml
  <head type=“main” rend = “align(center) bold”>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-head.html)

### Recipe Title - French

- ```xml
  <head type=“sub” rend = “align(center)”><foreign xml:lang=“fr”>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-head.html)

### Recipe Instruction References

- When a recipe's instruction references a previous recipe's instructions for how to complete the task

- ex. "proceed In exactly the same manner as for Apricot Syrup (see recipe)"

- If there is just the recipe title referenced put the `ptr` around that, if it says see recipe put the `ptr` around that.

- ```xml
  <ptr target="#<!-xml:id of the recipe referenced -->">(see recipe)</ptr>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-ptr.html)

### Section

- A section within a chapter for a group of like recipes

- ex. Cookies within the desserts category

- ```xml
  <div type="section">
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-div.html)

### Section Title

- The heading at the beginning of a section

- ```xml
  <head rend="align(center) case(allcaps) bold">
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-head.html)

### Word Standardization

- To indicate that there is a choice between what is on the page and what has been standardized

- enclose the version from the text in the `<sic>` tag and the standardized version in the `<corr>` tag

- ```xml
  <choice><sic>recipt</sic><corr>recipe</corr><choice>
  ```

- [TEI](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-choice.html)
