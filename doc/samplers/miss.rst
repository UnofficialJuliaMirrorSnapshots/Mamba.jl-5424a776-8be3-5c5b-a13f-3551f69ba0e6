.. index:: Sampling Functions; Missing Values Sampler

.. _section-MISS:

Missing Values Sampler (MISS)
-----------------------------

A sampler to simulate missing output values from their likelihood distributions.

Model-Based Constructor
^^^^^^^^^^^^^^^^^^^^^^^

.. function:: MISS(params::ElementOrVector{Symbol})

    Construct a ``Sampler`` object to sampling missing output values.  The constructor should only be used to sample stochastic nodes upon which no other stochastic node depends.  So-called 'output nodes' can be identified with the :func:`keys` function.  Moreover, when the ``MISS`` constructor is included in a vector of ``Sampler`` objects to define a sampling scheme, it should be positioned at the beginning of the vector.  This ensures that missing output values are updated before any other samplers are executed.

    **Arguments**

        * ``params`` : stochastic node(s) that contain missing values (``NaN``) to be updated with the sampler.

    **Value**

        Returns a ``Sampler{Dict{Symbol, MISSTune}}`` type object.

    **Example**

        See the :ref:`Bones <example-Bones>` and other :ref:`section-Examples`.

.. index:: Sampler Types; MISSTune

MISSTune Type
^^^^^^^^^^^^^

Declaration
```````````

``type MISSTune``

Fields
``````

* ``dims::Tuple`` : dimensions of a stochastic node to be updated.
* ``valueinds::Vector{Int}`` : indices to missing values in the node.
* ``distrinds::Vector{Int}`` : indices to node distributions from which to sample the missing values.
