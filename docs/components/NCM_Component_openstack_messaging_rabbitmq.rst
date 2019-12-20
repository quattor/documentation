##################################################
NCM\::Component\::openstack\::messaging - rabbitmq
##################################################

Types
-----

 - **/software/components/openstack/openstack_rabbitmq_config**
    - Description: Type to enable RabbitMQ and the message system for OpenStack.
    - */software/components/openstack/openstack_rabbitmq_config/user*
        - Description: RabbitMQ user to get access to the queue
        - Required
        - Type: string
        - Default value: openstack
    - */software/components/openstack/openstack_rabbitmq_config/password*
        - Required
        - Type: string
    - */software/components/openstack/openstack_rabbitmq_config/permissions*
        - Description: Set config/write/read permissions for RabbitMQ service. A regular expression matching resource names for which the user is granted configure permissions
        - Required
        - Type: string
