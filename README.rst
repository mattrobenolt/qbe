Django Query by Example (QBE)
=============================

:synopsis: Admin tool in order to get custom reports.

The objective of django-qbe is provide a assited and interactive way of making
complex queries with no technical knowledge (or minimal) to get custom reports
from the objects of Django models.

Based on QBE_ proposal from IBM®, django-qbe is intended to remove the
limitations of Django QuerySets objects and to use the whole expresive power of
the subjacent SQL.


Installation
------------

There's no setup.py script, neither easy_install yet, but I hope yes in the
near future. By the moment, you must download the *django_qbe* directory using
git::

  $ git clone git://github.com/versae/qbe.git
  $ copy -r qbe/django_qbe /path/to/your/project

And adding to the project settings::

  INSTALLED_APPS = (
      # [...] django builtins applications
      'django_qbe',
      # [...] Any other application
)

That's all. Then you can access to http://host:port/qbe
However, you can add a link from your admin page changing the admin index
template fo your AdminSite::

  class AdminSite(admin.AdminSite):
      index_template = "qbe_index.html"

Or adding in your custom admin index template the next javascript::

  <script type="text/javascript" src="{% url qbe_js %}"></script>


Settings
--------

The next lines show de available settings and its default values.

Enable autocompletion tool::

  QBE_AUTOCOMPLETE = True

Enable an Exhibit faceted navigation for results (not yet implemented)::

  QBE_EXHIBIT = False

Admin module name to add admin urls in results

  QBE_ADMIN = "admin"

Function to control to users with access to QBE

  QBE_ACCESS_FOR = lambda user: user.is_staff

Path to QBE formats export file, in order to add custom export formats::

  QBE_FORMATS_EXPORT = "qbe_formats"


.. _QBE: http://www.google.com/url?sa=t&source=web&ct=res&cd=2&ved=0CB4QFjAB&url=http%3A%2F%2Fpages.cs.wisc.edu%2F~dbbook%2FopenAccess%2FthirdEdition%2Fqbe.pdf&ei=_UD5S5WSBYP5-Qb-18i8CA&usg=AFQjCNHMv-Pua285zhWT8DevuZFj2gfYKA&sig2=-sTEDWjJhnTaixh2iJfsAw