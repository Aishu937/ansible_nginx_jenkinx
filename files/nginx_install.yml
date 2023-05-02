- name: Install Nginx and Jenkins
  hosts: server1
  become: true
  tasks:
    - name: Install Nginx on Ubuntu
      apt:
        name: nginx
        state: present
      when: ansible_distribution == "Ubuntu"

    - name: Install Nginx on CentOS
      yum:
        name: nginx
        state: present
      when: ansible_distribution == "CentOS"

    - name: Install Jenkins keyring on Ubuntu
      shell: curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
      when: ansible_distribution == "Ubuntu"

    - name: Install Jenkins repository on Ubuntu
      shell: echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
      when: ansible_distribution == "Ubuntu"

    - name: Install openjdk-11-jdk on Ubuntu
      apt:
        name: openjdk-11-jdk
        state: present
      when: ansible_distribution == "Ubuntu"

    - name: Update apt package cache
      apt:
        update_cache: yes

    - name: Install Jenkins on Ubuntu
      apt:
        name: jenkins
        state: present
      when: ansible_distribution == "Ubuntu"

    - name: Install Jenkins on CentOS
      yum:
        name: jenkins
        state: present
      when: ansible_distribution == "CentOS"

  handlers:
    - name: Restart Nginx
      service:
        name: nginx
        state: restarted

    - name: Enable Nginx and Jenkins services
      service:
        name: "{{ item }}"
        enabled: true
        state: started
      loop:
        - nginx
        - jenkins
