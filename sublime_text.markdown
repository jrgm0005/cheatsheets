# Sublime Text

## Sublime Text Packages

### User Binding Configuration
        
    [
     { "keys": ["ctrl+keypad_divide"], "command": "toggle_comment", "args": { "block": false } },
     { "keys": ["ctrl+shift+keypad_divide"], "command": "toggle_comment", "args": { "block": true } },
     { "keys": ["shift+f12"], "command": "goto_definition" },
     { "keys": ["ctrl+k"], "command": "reindent", "args": {"single_line": false} },
     { "keys": ["ctrl+shift+enter"], "command": "max_pane" },
     { "keys": ["super+alt+right"], "command": "shift_pane" },
     { "keys": ["super+alt+left"], "command": "unshift_pane" }
    ]


1. Emmet   (Improvement Development)
2. Docblockr (For documentation)
3. XDebug (php debugger)
4. BracketHighLighter (highlight the tabs)
5. Git && GitGutter
6. LocalHistory (For saving history of modified files)
7. Zeal (For documentation offline of languages)

    User Settings for ZEAL
    
        { 
        /**
          *  Zeal executable path.
          *  For Linux: /usr/bin/zeal
          *  For Windows: c:\\Program Files\\Zeal\\zeal.exe
          *  For Windows: C:\\Program Files (x86)\\Zeal\\zeal.exe
          */
          "zeal_command": "C:\\Program Files (x86)\\Zeal\\zeal.exe",
        
        /**
        * Sort mapping results.
        */
        
         "mapping_sort" : true,
        
         /**
          * Language mapping.
          */
         "language_mapping": {
           "HTML": {"lang": "html", "zeal_lang": "html"},
           "Angularjs": {"lang": "javascript", "zeal_lang": "angularjs"},
           "Jasmine": {"lang": "javascript", "zeal_lang": "jasmine"},
           "Javascript": {"lang": "javascript", "zeal_lang": "javascript"},
           "CSS": {"lang": "css", "zeal_lang": "css"},
           "PHP": {"lang": "php", "zeal_lang": "php"},
           "Python": {"lang": "python", "zeal_lang": "python"},
           "Ruby": {"lang": "ruby", "zeal_lang": "ruby"},
           "Rails": {"lang": "ruby", "zeal_lang": "rails"},
           "Docker": {"lang": "dockerfile", "zeal_lang": "docker"},
         }
        }

8. PlainTasks
9. ToDoReview
10. SideBar