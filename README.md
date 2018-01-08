## Integrating jupyter notebooks, reveal & github - Tests

testing how ipynb gets rendered in github & how to push a revealjs from notebook to github pages

### Reveal presentations can be made from notebooks with following extensions

#### RISE - has added "live mode" where users are able to execute notebook cells interactively within the presenation 
```
conda install -c damianavila82 rise -y
```
- take a look at [this video](https://www.youtube.com/watch?v=sXyFa_r1nxA&feature=youtu.be) to see how RISE works.

- RISE is pretty cool. It works like a kind of reveal preview mode. There does not seem to be a good export feature though.  It's clear that RISE won't host directly without a kernel running... but this could be a good use for a container.

#### nbpresent in the main jupyter extension
```
conda install -c conda-forge nbpresent -y
```
- I did not like working with this extension at all. It was very slow bulky hard to figure out. It also does not make simple reveal presentations the way I like, so I abandoned this extension and used the following method to create   

```
jupyter nbconvert --to slides Pandas_Stock_Panels.ipynb --reveal-prefix=reveal.js # you need the reveal.js present before rendering it

--SlidesExporter.reveal_scroll=True # is useful
--post serve # pushes to cdn for locally served copy
``` 


#### it's probaly a good idea to add the rest of jupyter extensions
```
conda install -c conda-forge jupyter_contrib_nbextensions -y
```

#### github & recent versions of git lab also render ipynb as static webpages with checkpoint/notebook cell outputs in tack.

### Github pages
Uses a Jekle themes, but can also anything static. Some constraints.
- The repo has to be made public as does the page
- Let's make a quick page for OAR [market structure](https://www.sec.gov/marketstructure/datavis.html)

jupyter nbconvert --to slides Pandas_Stock_Panels.ipynb --reveal-prefix=reveal.js

#### Notebooks can have custom logos & use css styles
to add a logo to a notebook just stick the following in the first cell
```

```

Can github pages use a custom css exported via nppresent?

- drop the css and py file same directory as the notebook with the following. 
```
from IPython.core.display import HTML


def style():
    css_file = './nb_styling.css'
    return HTML(open(css_file, "r").read())
```

Then just call you py in a cell of the notebook.
```
import oar_style; oar_style.style()
```


- play with some logos
- play with some css

### S3
Can S3 use a custom css exported via nppresent?
