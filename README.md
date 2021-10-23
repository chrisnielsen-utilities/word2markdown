# word2markdown
## Purpose
The purpose of this script is to convert a folder of MS Word documents into Markdown files that can be hosted on a GitHub Pages website.




### How to use
IMPORTANT: Make sure that the current website repository branch is set to `src` before running this script

First, populate the `input` folder with the desired subfolders and `.docx` word documents. The top level subfolders should represent the collections defined in the website `_config.yml`, see [here](https://github.com/chrisnielsen/chrisnielsen.github.io/blob/src/_config.yml#:~:text=collections%3A,news%3A) for examples of this. 

Each `.docx` Word document must follow the formatting rules:
1. The file name of the .docx document will be used as the associated web page title
2. The allowed `.docx` styles are `Normal`, `Title`, `Heading 1`, `Heading 2`, `Heading 3`, `List Bullet`, and `List Number`
3. All documents should have their MathType equations converted into `MathJax:LaTeX` by clicking the `Convert Equations` button and selecting `MathJax:LaTeX` from the MathType translator dropdown menu
4. To ensure that a math equation is centered, make sure that there are line breaks to the top and bottom of the equation in the document
5. Use common Markdown syntax to bold, italic, and apply other modifications to text in the `.docx` document
6. For each image in the document, write the following above the image: `Figure__width-in-pixels__figure-name`, where `width-in-pixels` specifies the width in pixels for the image on the web page and `figure-name` specifies the figure name for the image which will be shown below the image in the Markdown document
7. For `projects` documents, the first paragraph in the `.docx` file will be used as the abstract displayed on the `projects` page
8. All hyperlinks must be removed in the `.docx` file

Next, run the Python notebook `process_documents.ipynb`. The path to the website repository must be specified using the `repo_path` variable defined at the top of the notebook. Running this notebook will process all documents located in the `input` folder, storing the processed results in the `output` folder. Then the `output` folder will be merged with the `repo_path` folder to update the website contents. This merge process will replace existing files with the same file names but will not delete any preexisting files in the website directory. After the notebook is run, the `src` branch can be pushed and `./bin/deploy` can be run to deploy the website.




### Important gotchas
1. To ensure the Markdown output is encoded in UTF-8, make sure that when writing the file to disk that you include the argument `encoding='utf8'` 



### Data provided in repo
There is two sets of example data provided in this repo:
1. The `input` folder contains the current subfolders and documents used by my website
2. The `input_test` folder contains a number of subfolders and documents created to test the system 
