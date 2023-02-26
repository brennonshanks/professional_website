---
# An instance of the Experience widget.
# Documentation: https://wowchemy.com/docs/page-builder/
widget: experience

# This file represents a page section.
headless: true

# Order that this section appears on the page.
weight: 40

title: Employment
subtitle: Research Experience

# Date format for experience
#   Refer to https://wowchemy.com/docs/customization/#date-format
date_format: Jan 2006

# Experiences.
#   Add/remove as many `experience` items below as you like.
#   Required fields are `title`, `company`, and `date_start`.
#   Leave `date_end` empty if it's your current employer.
#   Begin multi-line descriptions with YAML's `|2-` multi-line prefix.
experience:
  - title: Applied Scientist Intern
    company: Amazon Web Services
    company_url: ''
    company_logo: 
    location: Cambridge, United Kingdom
    date_start: '2022-06-01'
    date_end: ''
    description: ''

  - title: Doctoral Placement Researcher
    company: Secondmind
    company_url: https://www.secondmind.ai/
    company_logo: 
    location: Cambridge, United Kingdom
    date_start: '2021-10-01'
    date_end: '2022-05-01'
    description: |2-
        I was a Student Researcher at [Secondmind](https://www.secondmind.ai/) (formerly known as PROWLER.io), a machine learning technology start-up based in Cambridge, UK with a strong focus on basic research and an excellent track record of scientific publications in the areas of *Gaussian processes*, *variational inference*, and *Bayesian optimization* (you may know them by their popular open-source library, [GPFlow](https://github.com/GPflow/GPflow)).

  - title: Applied Scientist Intern
    company: Amazon Web Services
    company_url: ''
    company_logo: 
    location: Berlin, Germany
    date_start: '2019-06-01'
    date_end: '2019-12-01'
    description: |2-
        I spent the Summer-Fall of 2019 at Amazon in Berlin, Germany, conducting research in the area of [AutoML](/tag/automl/) in contribution to the [Automatic Model Tuning](https://arxiv.org/abs/2012.08489) service on [AWS SageMaker](https://aws.amazon.com/sagemaker/). I was fortunate to been given the opportunity to work with eminent researchers in the field, [Matthias Seeger](https://mseeger.github.io/), [Aaron Klein](https://aaronkl.github.io/), and [Cédric Archambeau](http://www0.cs.ucl.ac.uk/staff/c.archambeau/). Together, we tackled the challenges of extending *multi-fidelity Bayesian optimization* with *asynchronous parallelism*. The research developed during my internship culminated in a [research paper](publication/async-multi-fidelity-hpo/) and the release of our [code](https://autogluon.mxnet.io/api/autogluon.searcher.html#gpmultifidelitysearcher) as part of the open-source [AutoGluon](https://github.com/awslabs/autogluon) library.

  - title: Software Engineer
    company: CSIRO's Data61
    company_url: https://data61.csiro.au/
    company_logo: 
    location: Sydney, Australia
    date_start: '2016-07-01'
    date_end: '2019-04-01'
    description: |2-
        After NICTA was subsumed under CSIRO (Australia's national science agency), I continued as a member of the [Inference Systems Engineering](#) team, working to apply probabilistic machine learning to a multitude of problem domains, including spatial inference and Bayesian experimental design, with an emphasis on scalability. In this time, I led the design and implementation of new [microservices](https://data61.csiro.au/en/Our-Research/Our-Work/Safety-and-Security/Understanding-Risk/Determinant) and contributed to the development of [open-source libraries](https://github.com/gradientinstitute/aboleth) for large-scale Bayesian deep learning.

         During this period, I also served a brief stint with the [Graph Analytics Engineering](#) team (the team behind [StellarGraph](https://www.stellargraph.io/)), where I contributed to research into *graph representation learning* from a probabilistic perspective. These efforts culminated in a [research paper](publication/vi-gcn-2/) that went on to be awarded a spotlight presentation at the field's [premier conference](https://proceedings.neurips.cc/paper/2020).

  - title: Software Engineer
    company: National ICT Australia (NICTA)
    company_url: ''
    company_logo: 
    location: Sydney, Australia
    date_start: '2015-05-01'
    date_end: '2016-06-30'
    description: |2-
        As a software engineer with a specialization in machine learning, I was a member of a team of machine learning researchers and engineers engaged in an interdisciplinary collaboration with leading researchers from multiple areas of the natural sciences, as part of the [Big Data Knowledge Discovery](https://research.csiro.au/data61/big-data-knowledge-discovery/)   initiative sponsored by the [Science Industry Endowment Fund (SIEF)](https://sief.org.au/). During this time I helped lead the development and release of numerous [open-source libraries](https://github.com/NICTA/revrand) for applying Bayesian machine learning at scale.

  - title: Research Intern
    company: Commonwealth Scientific and Industrial Research Organisation (CSIRO)
    company_url: https://www.csiro.au/
    company_logo: 
    location: Sydney, Australia
    date_start: '2013-11-01'
    date_end: '2014-02-01'
    description: |2-
        I joined the CSIRO's Language and Social Computing team as a Summer Vacation Scholar for the summer of 2013-14 and worked on applying machine learning and natural language processing (NLP) techniques to develop a text classification system for automated *sentiment analysis*.

# - title: PhD Candidate
#   company: University of Sydney
#   company_url: https://sydney.edu.au/
#   company_logo: usyd
#   location: Sydney, Australia
#   date_start: '2018-01-01'
#   date_end: ''
#   description: ''

design:
  columns: '2'
---
