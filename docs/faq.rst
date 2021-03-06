FAQ
===
You will find a lot of useful information in the `documentation
<https://django-elasticsearch-dsl-drf.readthedocs.io/>`__.

Additionally, all raised issues that were questions have been marked as
`question`, so you could take a look at the
`closed (question) issues <https://github.com/barseghyanartur/django-elasticsearch-dsl-drf/issues?q=is%3Aissue+label%3Aquestion+is%3Aclosed>`__.

Questions and answers
---------------------

**Question**

- Is it possible to search sub string in word?
- How to implement partial/fuzzy search?

**Answer**

Yes. There are many ways doing this in Elasticsearch.

To mention a couple:

- You could use partial matching using NGrams. Partially shown
  `here <https://django-elasticsearch-dsl-drf.readthedocs.io/en/0.17.2/advanced_usage_examples.html?highlight=ngram#id8)>`__.
  `The basic idea <https://www.elastic.co/guide/en/elasticsearch/guide/current/_ngrams_for_partial_matching.html>`__.
- Use `contains <https://django-elasticsearch-dsl-drf.readthedocs.io/en/latest/filtering_usage_examples.html?highlight=contains#contains>`__
  functional filter.

----

**Question**

Can we use Django REST Framework ``serializers.ModelSerializer`` directly?

**Answer**

No, but you could use ``serializers.Serializer``. `Read the docs
<https://django-elasticsearch-dsl-drf.readthedocs.io/en/latest/quick_start.html?highlight=serializer#serializer-definition>`__.

----

**Question**

How can I order search results overall relevance

**Answer**

That's ``_score``. See the following `example
<https://github.com/barseghyanartur/django-elasticsearch-dsl-drf/blob/master/examples/simple/search_indexes/viewsets/book/frontend.py#L206>`__.

.. code-block:: python

    ordering = ('_score', 'id', 'title', 'price',)

In the given example, results are sorted by the ``score`` (which is relevance),
then by ``id``, ``title`` and ``price``.

----

**Question**

How can I separate my development/production/acceptance/test indexes?

**Answer**

It's documented `here <https://django-elasticsearch-dsl-drf.readthedocs.io/en/latest/quick_start.html#settings>`__.

----

**Question**

How can I sync my database with Elasticsearch indexes.

**Answer**

It's documented `here <https://django-elasticsearch-dsl-drf.readthedocs.io/en/latest/quick_start.html#sample-partial-sync-using-custom-signals>`__.

----

**Question**

I keep getting ``[FORBIDDEN/12/index read-only / allow delete (api)]`` error
when  saving models despite having ``blocks={'read_only_allow_delete': None}``,
in settings.

**Answer**

Once of the possible reasons for the mentioned symptom might be `low disk space
<https://discuss.elastic.co/t/forbidden-12-index-read-only-allow-delete-api/110282>`__.
