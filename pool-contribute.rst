Contribute to the Pool
======================

The official pool at `https://github.com/horizon-eda/horizon-pool/ <https://github.com/horizon-eda/horizon-pool/>`__ lives from it's user
contributions. There are multiple ways you can help. The most obvious one is
by submitting parts you made.

To keep the pool nice an clean, only add parts you can actually buy with
their corresponding symbols, entities, etc. So don't add some part
called 7805, instead add a MC7805BDTRKG manufactured by ON
Semiconductor. Once you created something you'd like to share, you can use the
:doc:`Pool Manager <pool-mgr>` to upload your creation to the offical pool:

Using the GitHub integration.
-----------------------------

For the GitHub integration to work, the pool has to be downloaded using
the "Download..." button on the start Page of the pool manager. The pool
manager will clone the global pool into the ``.remote`` directory in
your local pool. If all goes right, you should never need to touch that
directory. Two operations are available for keeping your local copy
up-to-date and merging your parts into the global pool

Upgrade pool
~~~~~~~~~~~~

This will update your copy of the global pool in the ``.remote``
directory to the latest commit and ask you which changes you'd like to
have applied to your local pool.

Create pull request
~~~~~~~~~~~~~~~~~~~

First, add the Parts/Entities/etc. to the "items to be merged" list,
then fill in Pull Request title and body. The pool manager will
automatically add items that are needed to not break references. So if
you create an all-new Part with new Unit, Entity and Package, these will
get added to the list when you add the Part. Don't forget to add the new
symbols. After making sure that this is what you want, click the "Create
pull request" button. You'll be prompted for your GitHub credentials as
well as your name and email address for the commit author information.

Helping by reviewing
~~~~~~~~~~~~~~~~~~~~

Adding parts is a great thing, but checking parts other people made could be a 
good thing as well. More eyes that crosscheck a part against its datasheet will
decrease the chance of something that works. If you successfully produced a PCB
with certain parts on it, you can say something about solderability as well and
this is a stronger indicator, that the part has no critical mistakes.
