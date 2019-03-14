Ansible Role: tamay.firewalld
=========

This role configures firewalld. 

Requirements
------------

None.

Role Variables
--------------

List of all variables, including default values.

    firewalld_service:
      - service: http
        state: enabled
        zone: public
      - service: http
        state: enabled
        zone: dmz
      - service: https
        state: disabled

List of services to enable or disable. **State** defaults to *disabled*, and **zone** defaults to *public*. Both can be omitted. Services as defined in ```firewall-cmd --get-services```.
    
    firewalld_port: []
    # Example:
    #firewalld_port:
    #  - port: 8888/tcp
    #    state: enabled
    #    zone: public

List of ports in **PORT/PROTO** format to enable or disable. **State** defaults to *disabled*, and **zone** defaults to *public*. Both can be omitted. 

Dependencies
------------

None.

Example Playbook
----------------

    ---
    
    - hosts: all
    
      vars:
        firewalld_service:
          - service: http
          - service: http
            zone: dmz
          - service: https
            state: disabled
        firewalld_port:
          - port: 8888/tcp
    
      roles:
      - tamay.firewalld

License
-------

MIT

Author Information
------------------

tamay.mueller@gmail.com