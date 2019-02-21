# csi
CSI-Plugin
# Datera CSI Driver Deployment Yaml
#
# Documentation on how to write this insanity:
# https://github.com/kubernetes/community/blob/master/contributors/design-proposals/storage/container-storage-interface.md#recommended-mechanism-for-deploying-csi-drivers-on-kubernetes
#
# Pieces
# ------
# * datera storage class
# CONTROLLER
# * csi-provisioner
#   . provisioner service account
#   . provisioner cluster role
#   . provisioner cluster role binding
#   . provisioner service
#   . provisioner statefulset
# * csi-attacher
# * csi-snapshotter
# * datera-plugin (controller)
# NODE
# * driver-registrar
#   . driver-registrar service account
#   . driver-registrar cluster role
#   . driver-registrar cluster role binding
#   . driver-registrar service?
#   . driver-registrar daemonset
# * iscsid
# * datera-plugin (node/identity)
#
#
# #################################
# StorageClass Supported Parameters
# #################################
# Name                 Default
# -------------        ------------
# replica_count        3
# placement_mode       hybrid
# ip_pool              default
# template             ""
# round_robin          false
# read_iops_max        0
# write_iops_max       0
# total_iops_max       0
# read_bandwidth_max   0
# write_bandwidth_max  0
# total_bandwidth_max  0
# iops_per_gb          0
# bandwidth_per_gb     0
# fs_type              ext4
# fs_args              -E lazy_itable_init=0,lazy_journal_init=0,nodiscard -F
# delete_on_unmount    false
#
#
# Currently datera UDC environment variables are used to initialize the driver
# (This may change in the future)
#
# DAT_MGMT
# DAT_USER
# DAT_PASS
# DAT_TENANT
# DAT_API
#
# These need to be set for both the controller StatefulSet and node DaemonSet
Reference https://github.com/Datera/datera-csi/blob/master/deploy/kubernetes/with-host-iscsid/csi-datera-latest.yaml
