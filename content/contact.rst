public: yes
location: 'contact'
form:
  - email: 'pod@aliceandmia.com'
    next: 'thanks'
    submit: 'send it!'


*******************
Contact Alice & Mia
*******************


.. callmacro:: contact.macros.j2#show_form
  :slug: 'contact'
  :data: 'form'
