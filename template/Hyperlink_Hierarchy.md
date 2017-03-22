# Contributing to *An Introduction to Applied Bioinformatics*

*An Introduction to Applied Bioinformatics* (IAB), is an open source project and we welcome community contributions. Contributions should generally be made in the form of GitHub pull requests. We've simplified the process of submitting these for changes to the IAB content, as described below.

You will need a (free) GitHub account to submit a pull request.

## How IAB is developed

IAB is written in [markdown](http://commonmark.org/). [build-iab](https://github.com/caporaso-lab/build-iab) is then used to convert that markdown to html (for static online viewing) and ipynb (for interactive use). If you're submitting changes to content, you'll be submitting changes to markdown files. These are much more manageable that submitting changes to IPython notebooks, as it's much easier to diff the content.


## Technical points

### Building IAB locally

If you're interested in building the IAB html and/or IPython Notebooks locally, you'll need to install IAB and build-iab. You can do this as follows:

```
pip install numpy
pip install https://github.com/caporaso-lab/build-iab/archive/master.zip
wget https://github.com/caporaso-lab/An-Introduction-To-Applied-Bioinformatics/archive/master.zip
unzip master.zip
cd An-Introduction-To-Applied-Bioinformatics-master/
pip install .
```

Then, to build the IPython Notebooks, you can run:

```
biab notebook -i book -o ipynb
```

or to build the HTML version, you can run:

```
biab html -i book -o html
```

### Linking to other sections of the text

All section headings must have ids associated with them. Should be generated as follows:

```bash
$ biab idgen
<link src="9mM4Bb"/>
```

When you define a section heading, you'd end it with the tag returned from the above command. For example:

```markdown
## Some section <link src="9mM4Bb"/>
```

If you then wanted to link to that section from somewhere else in the text, you could do that with a markdown link as follows:

```markdown
This concept is discussed in further detail [above](alias://9mM4Bb).
```

You should always link using these ids, and never statically link to other sections of the text with URLs (because a section name might change, but its id won't).

## License and license changes

The IAB license is available [here](https://github.com/caporaso-lab/An-Introduction-To-Applied-Bioinformatics/blob/master/LICENSE). This license may change over time, but the online version of IAB will always be the most current version, and will be available free of charge.

By contributing to IAB, you are agreeing that Greg Caporaso has sole discretion over the license and any future changes to the license. If a paid (e.g., printed) copy of IAB is ever created, contributors are not entitled to payments or royalties of any kind. Your contribution of content represents your agreement with these terms.
