
# To-Do List for MariaDB Secure Installation

1. **Copy the secure installation script**
    - **Task**: Copy the secure installation script to the target machine.
    - **Details**:
        ```yaml
        - name: Copy the secure installation script
          copy:
            content: |
              #!/bin/bash
              sudo mariadb-secure-installation <<EOF
              n
              {{ mariadb_root_password }}
              {{ mariadb_root_password }}
              y
              y
              y
              y
              EOF
            dest: /tmp/mariadb_secure.sh
            mode: '0755'
        ```

2. **Run the MariaDB secure installation script**
    - **Task**: Execute the secure installation script on the target machine.
    - **Details**:
        ```yaml
        - name: Run the MariaDB secure installation script
          command: /tmp/mariadb_secure.sh
          ignore_errors: yes
        ```

3. **Delete the secure installation script**
    - **Task**: Remove the secure installation script from the target machine.
    - **Details**:
        ```yaml
        - name: Delete the secure installation script
          file:
            path: /tmp/mariadb_secure.sh
            state: absent
        ```








































