# Colouring cities kick off meeting 5th January 2021

## Proposed REG tasks

- Some more specific details than the below in [this issue](https://github.com/colouring-london/colouring-london/issues/680)
- Server VM setup/management
  - Review what has already been set up on 
  - Improve the automation of (re)provisioning a VM for London and prepare whole VM template for other cities.
- Automate CI/deployment pipelines:
  - Build and release from GitHub to staging/production through GitHub Actions (currently only a CI task is set up)
  - Think about some automation of database schema updates and better db migrations setup (currently all manual / git-based)
- Improve testing setup (currently only a few unit tests)
  - Help set up an integration testing environment/pipeline (would help greatly for automated dependency updates)
  - Help set up front-end testing 
- Tile server improvements - the tile server is a custom implementation in Node+Mapnik due to having to render building data visualisation as raster tiles because of OS licensing.
  - Review if possible to use a more off-the-shelf solution that would help with the below points, or
  - Improve tile cache control, build utilities for easier clearing of cache for selected layers, regions, etc
  - Add some request priority control, which would help with keeping the app smooth (as even things like building selection highlight is sent as raster, again due to OS limitations)
  - Build a way for less technical users to easily edit data map styles. Currently works by editing Mapnik XML files - sometimes hard even for programmers. E.g. look at whether it's possible to combine the raster tiles requirement with a style specification like the Mapbox JSON, which can be edited with GUI tools like Maputnik



## Notes

Generating data computationally through inference (AI)

- not front-end
- but back-end management or data merging/inference?
- We are trying to infer things that the tax office has on buildings based on age, then get citizens (locals) to check these things (crowdsourcing)
- The site is a tool for the crowdsourcing, like with openstreetmap, the dataset is the product
- relation to the historial maps project
- layer one or two historical maps into the system
- proving a point that open data is worth it
- Meet with Tom on technical side of things
    - Working practices, github, slack etc
- Mateusz on front-end updates for new data requirements
- Is all data crowdsourced apart from the Ordnance Survey polygons?

# Meeting 11th January

## Questions

- What is Tom/Mateusz role for the project duration?
    - Minimal, can giver overview
    - Mateusz (still working on, not regular) and Matcheck, worked on dev work more recently
- **EC:** Get Tom Russel or Mateusz Konieczny to add EC as contributor to [repo](https://github.com/colouring-london/colouring-london)
- **EC:** Also get one of them to show EC VM setup/management (Azure?)
- **EC:** Should I use an existing project board?
    - If not I will create GH issues for above tasks and set up project board (follow [template](https://github.com/colouring-london/colouring-london/projects) in the colouring-london repo)
    - Prioritise and have milestones (dates) signed off by team
    - I should probably set up my own project board and break down Polly's 
    - Might be worth sorting through the open issues in a session
    - Milestones aren't useful and could probably be deleted
- Think about GH branches, contributor guidelines
     - Set up blocks to mergeing
     - Document this and so we can have release branch, especially if there is a Terraform

## Notes

- Room for improvement around integration and deployment, so currently, there is VM with the repo cloned and setup carried out
- Terraform and Ansible setup scripts would be super valuable but not urgent
- Would be useful to help me understand the setup
- I should have access to the VM in Turing - get access to colouring London subscription at Turing Azure
- setup of website: https://github.com/colouring-london/colouring-london/blob/master/docs/setup-production-environment.md 
- deploy template: https://github.com/colouring-london/colouring-london/issues/new?assignees=&labels=&template=deploy.md&title= 
- ^ template when you make a new issue
- VMs each have IP addresses, might need to get Azure to manage the DNS record to associate IP with domain (test with staging)
- Big priority task: updating the polygons, with the latest OS (2021), currently 2016 - first task after familiarisation with codebase
    - Include method to auto-update/build the colouring london dataset with new OS releases
- Take the OS polygons as buildings (ignore the philosophical implications)

## EC TODOs week 10th Jan:

1. [ ] Run colouring London locally
2. [x] Request to be in colouring London Azure sub with IT
3. [ ] Log into the VM and see what the commit of the repo the setup was done at
4. [ ] Propose in the Friday meeting to have a mega sort-through session of issues in order for me (Ed) to have a project board for the 8 months (any timelined milestones, but ideally just project board unless there are specific deadlines for things)
5. [ ] Perhaps try a fresh setup on another VM? (this will help with the Terraform-ing)
6. [ ] Should we set up github discussions

## Meeting 14th Jan

- Only Matchek as access to the Azure, Polly should email instroducing us, he is no longer funded on the project
- doodle for the 2hr session
- Look at Mateusz PR?
- using the OSM for testing 
- Mateusz has docs for the VMs setup
- The terraform stuff can be based on stuff in here: https://github.com/colouring-london/colouring-london-config 
- there's also a vagrant script: https://github.com/colouring-london/colouring-london/blob/master/provision/vm_provision.sh
- Documentation could be a big thing to work on, but not the readthedocs as no docstrings
- There is a wiki (no info) that could be for entire projects - gitbook maybe? Have a look at the options, needs to be not too hard for Polly to edit
- Maybe look at the issues and add the below if not already there:

Main priorities:
- Documentation in the README and docs
    - Find everything from readme
    - Docstrings wherever possible
    - *gibook for a later date*
- Updating the setup (terraform)
- Updating the polygons
