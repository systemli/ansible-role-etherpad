ansible-etherpad
================

Role to install & maintain Etherpad Lite

Role Variables
--------------

The playbook requires no special configuration, but offers a bunch of options.

**Important**: You must set the `etherpad_api_key`!

Defaults:

    etherpad_required_packages:
      - nodejs
      - nodejs-legacy
      - npm
      - git
    etherpad_repository: "https://github.com/ether/etherpad-lite.git"
    etherpad_repository_key_file: ""
    etherpad_repository_version: "master"
    etherpad_user: "etherpad"
    etherpad_group: "{{ etherpad_user }}"
    etherpad_home: "/home/etherpad"
    etherpad_path: "{{ etherpad_home }}/etherpad-lite"
    etherpad_console_path: "{{ etherpad_home }}/etherpad-lite-console"
    etherpad_title: "Etherpad"
    etherpad_favicon: "favicon.ico"
    etherpad_ip: 0.0.0.0
    etherpad_port: 9001
    etherpad_db_type: redis #alternative: dirty or mysql
    # Setting for Redis
    etherpad_db_settings:
      host: localhost
      port: 6379
      database: 0
    # Setting for dirty.db
    #etherpad_db_settings:
      #filename: "var/dirty.db"
    # Setting for MySQL
    #etherpad_db_settings:
      #user: "root"
      #host: "localhost"
      #password: "password"
      #database: "store"
    etherpad_users: []
      #  -
      #    name: admin
      #    password: ""
      #    is_admin: "true"
    etherpad_api_key: ""
    etherpad_session_key: "Y7sc5qSXw5aEBIDGsjfkyLJDV"
    etherpad_disable_ip_logging: "true"
    etherpad_default_text: '"Welcome to Etherpad!\\n\\nThis pad text is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents!\\n\\nGet involved with Etherpad at http:\\/\\/etherpad.org\\n"'
    etherpad_pad_options_no_colors: "false"
    etherpad_pad_options_show_controls: "true"
    etherpad_pad_options_show_chat: "true"
    etherpad_pad_options_show_line_numbers: "true"
    etherpad_pad_options_use_monospace_font: "false"
    etherpad_pad_options_user_name: "false"
    etherpad_pad_options_user_color: "false"
    etherpad_pad_options_rtl: "false"
    etherpad_pad_options_always_show_chat: "false"
    etherpad_pad_options_chat_and_users: "false"
    etherpad_pad_options_lang: "en-gb"
    etherpad_suppress_errors_in_pad_text: "false"
    etherpad_require_session: "false"
    etherpad_edit_only: "false"
    etherpad_session_no_password: "false"
    etherpad_minify: "true"
    etherpad_max_age: 21600
    etherpad_abiword: "null"
    etherpad_allow_unknown_file_ends: "true"
    etherpad_require_authentication: "false"
    etherpad_require_authorization: "false"
    etherpad_trust_proxy: "false"
    etherpad_log_level: "INFO"
    etherpad_log_appenders:
      -
        type: console
    etherpad_socket_transport_protocols: ["xhr-polling", "jsonp-polling", "htmlfile"]
    etherpad_load_test: "false"
    etherpad_toolbar:
      left:
        - ["bold", "italic", "underline", "strikethrough"]
        - ["orderedlist", "unorderedlist", "indent", "outdent"]
        - ["undo", "redo"]
        - ["clearauthorship"]
      right:
        - ["importexport", "timeslider", "savedrevision"]
        - ["settings", "embed"]
        - ["showusers"]
      timesloder:
        - ["timeslider_export", "timeslider_returnToPad"]
    etherpad_console_enabled: False
    etherpad_monit_enabled: False

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: 0x46616c6b.etherpad }

License
-------

GPLv3
