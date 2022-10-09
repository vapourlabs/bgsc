.. _ref_intro:

Beginners Guide to Systems Coding
=================================

.. admonition:: Note from the developers

   This guide is still under development. There may be grammatical errors
   and typos present. If you find either, please write a commit to
   appropriately resolve them.

Welcome to the DCS World Beginners Guide to Systems Coding!

For a long time, we've seen rapid growth in the DCS modding communty. Many
modders have begun creating flyable aircraft that utilise their own 3D models,
weapon loadouts and flight models. But out of all these new mods, only a mere
fraction of them have what we call an **External Systems Model**. (ESM)
ESMs are responsible for allowing developers to write their own systems code
in their mod, such as animating the movement of landing gears, implementing 
weapon systems and having working avionics.

Instead of calling this the "Beginners Guide to ESM Development," we're going
to keep it nice, sweet and short with calling it "systems coding". The
goal of this guide is to educate DCS modders how to develop custom systems and
incorporate them into their mods. Going headfirst into systems coding can be
frightening at first, so it is our mission to make easily digestible for
beginners.

Prerequisites
-------------

Before you can get started coding systems into your DCS mods, there are a set
of prerequisites that we expect everyone who reads the guide to pass:

- You must have a basic understanding of creating a mod structure. It's
  important to understand how to design the architecture of your mod's
  codebase.
- **You need to have a basic understanding of programming.** This is an 
  absolute requirement for systems coding. If you don't know how to code, you
  won't know how to work around and solve problems in your system scripts.
- Lacking an understanding or skillset in 3D animating is detrimental to
  writing animation-based systems code. Here is a `good starting point
  <https://www.megabotix.com/wp-content/uploads/dcs/animation-dcs.mp4>`_ for
  learning how to animate 3D models for DCS World.

Table of Contents
-----------------

.. toctree::
   :maxdepth: 2
   
   contributions
   api/index

Search
------

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
