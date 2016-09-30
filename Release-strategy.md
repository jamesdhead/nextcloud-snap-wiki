# Definitions

*Branches* are Github branches, either in this repository or in the nextcloud/server one.

*Channels* are Ubuntu store channels which can be selected by the user when installing a Snap

# Mapping

We will have the following mapping between branches and channels:

* Branches -> Channels
* master -> stable
* develop -> candidate
* stable10-daily via cronjob -> beta
* master-daily via cronjob -> edge

So the candidate channel is being used to test new Snap features, while the beta and edge channels can be used to test new Nextcloud features