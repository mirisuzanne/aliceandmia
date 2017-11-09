public: yes
location: 'contact'
hide_title: yes
form:
  - email: 'pod@aliceandmia.com'
    next: 'thanks'
    submit: 'send it!'
summary: |
  Have a question for our podcast,
  a topic you'd like us `to write about`_,
  or just want to say hi?
  **Leave us a note here**,
  or send an email to `pod@aliceandmia.com`_.

  .. _`pod@aliceandmia.com`: mailto:pod@aliceandmia.com
  .. _to write about: /tags/Writing/


**********
Contact Us
**********

.. callmacro:: contact.macros.j2#show_form
  :slug: 'contact'
  :data: 'form'
