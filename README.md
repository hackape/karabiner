```json
// ~/.config/karabiner/karabiner.json

{
  "global": {
    "check_for_updates_on_startup": true,
    "show_in_menu_bar": true,
    "show_profile_name_in_menu_bar": false
  },
  "profiles": [
    {
      "complex_modifications": {
        "parameters": {
          "basic.simultaneous_threshold_milliseconds": 50,
          "basic.to_delayed_action_delay_milliseconds": 500,
          "basic.to_if_alone_timeout_milliseconds": 1000,
          "basic.to_if_held_down_threshold_milliseconds": 500,
          "mouse_motion_to_scroll.speed": 100
        },
        "rules": [
          {
            "description": "Fn Lock: Double tab fn key to toggle between standard f1-f12 keys and media control keys",
            "manipulators": [
              {
                "description": "2nd press, fn_lock=0",
                "conditions": [
                  {
                    "name": "fn_pressed",
                    "type": "variable_if",
                    "value": 1
                  },
                  {
                    "name": "fn_lock",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "fn",
                  "modifiers": {
                    "optional": ["any"]
                  }
                },
                "to": [
                  {
                    "set_variable": {
                      "name": "fn_lock",
                      "value": 0
                    }
                  }
                ],
                "type": "basic"
              },
              {
                "description": "2nd press, fn_lock=1",
                "conditions": [
                  {
                    "name": "fn_pressed",
                    "type": "variable_if",
                    "value": 1
                  },
                  {
                    "name": "fn_lock",
                    "type": "variable_unless",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "fn",
                  "modifiers": {
                    "optional": ["any"]
                  }
                },
                "to": [
                  {
                    "set_variable": {
                      "name": "fn_lock",
                      "value": 1
                    }
                  }
                ],
                "type": "basic"
              },
              {
                "description": "1st press, set fn_pressed intermediate var",
                "from": {
                  "key_code": "fn",
                  "modifiers": {
                    "optional": ["any"]
                  }
                },
                "to": [
                  {
                    "set_variable": {
                      "name": "fn_pressed",
                      "value": 1
                    }
                  },
                  {
                    "key_code": "fn"
                  }
                ],
                "to_delayed_action": {
                  "to_if_canceled": [
                    {
                      "set_variable": {
                        "name": "fn_pressed",
                        "value": 0
                      }
                    }
                  ],
                  "to_if_invoked": [
                    {
                      "set_variable": {
                        "name": "fn_pressed",
                        "value": 0
                      }
                    }
                  ]
                },
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "fn_lock",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "f1"
                },
                "to": [
                  {
                    "key_code": "display_brightness_decrement"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "fn_lock",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "f2"
                },
                "to": [
                  {
                    "key_code": "display_brightness_increment"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "fn_lock",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "f7"
                },
                "to": [
                  {
                    "key_code": "rewind"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "fn_lock",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "f8"
                },
                "to": [
                  {
                    "key_code": "play_or_pause"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "fn_lock",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "f9"
                },
                "to": [
                  {
                    "key_code": "fastforward"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "fn_lock",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "f10"
                },
                "to": [
                  {
                    "key_code": "mute"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "fn_lock",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "f11"
                },
                "to": [
                  {
                    "key_code": "volume_decrement"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "fn_lock",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "f12"
                },
                "to": [
                  {
                    "key_code": "volume_increment"
                  }
                ],
                "type": "basic"
              }
            ]
          },
          {
            "description": "Change Left Control + Right Control to Caps Lock",
            "manipulators": [
              {
                "from": {
                  "key_code": "right_control",
                  "modifiers": {
                    "mandatory": ["left_control"],
                    "optional": ["any"]
                  }
                },
                "to": [
                  {
                    "key_code": "caps_lock"
                  }
                ],
                "type": "basic"
              }
            ]
          },
          {
            "description": "Numeric Keypad Mode [Tab as trigger key]",
            "manipulators": [
              {
                "from": {
                  "key_code": "tab"
                },
                "to": [
                  {
                    "set_variable": {
                      "name": "numeric_keypad_mode",
                      "value": 1
                    }
                  }
                ],
                "to_after_key_up": [
                  {
                    "set_variable": {
                      "name": "numeric_keypad_mode",
                      "value": 0
                    }
                  }
                ],
                "to_if_alone": [
                  {
                    "key_code": "tab"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "7"
                },
                "to": [
                  {
                    "key_code": "delete_or_backspace"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "8"
                },
                "to": [
                  {
                    "key_code": "keypad_equal_sign"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "9"
                },
                "to": [
                  {
                    "key_code": "keypad_slash"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "0"
                },
                "to": [
                  {
                    "key_code": "keypad_asterisk"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "u"
                },
                "to": [
                  {
                    "key_code": "keypad_7"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "i"
                },
                "to": [
                  {
                    "key_code": "keypad_8"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "o"
                },
                "to": [
                  {
                    "key_code": "keypad_9"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "p"
                },
                "to": [
                  {
                    "key_code": "keypad_hyphen"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "j"
                },
                "to": [
                  {
                    "key_code": "keypad_4"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "k"
                },
                "to": [
                  {
                    "key_code": "keypad_5"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "l"
                },
                "to": [
                  {
                    "key_code": "keypad_6"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "semicolon"
                },
                "to": [
                  {
                    "key_code": "keypad_plus"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "m"
                },
                "to": [
                  {
                    "key_code": "keypad_1"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "comma"
                },
                "to": [
                  {
                    "key_code": "keypad_2"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "period"
                },
                "to": [
                  {
                    "key_code": "keypad_3"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "slash"
                },
                "to": [
                  {
                    "key_code": "keypad_period"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "spacebar"
                },
                "to": [
                  {
                    "key_code": "keypad_0"
                  }
                ],
                "type": "basic"
              },
              {
                "conditions": [
                  {
                    "name": "numeric_keypad_mode",
                    "type": "variable_if",
                    "value": 1
                  }
                ],
                "from": {
                  "key_code": "right_alt"
                },
                "to": [
                  {
                    "key_code": "keypad_period"
                  }
                ],
                "type": "basic"
              }
            ]
          },
          {
            "description": "Change right_command+ijkl to arrow keys",
            "manipulators": [
              {
                "from": {
                  "key_code": "i",
                  "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                  }
                },
                "to": [
                  {
                    "key_code": "up_arrow"
                  }
                ],
                "type": "basic"
              },
              {
                "from": {
                  "key_code": "j",
                  "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                  }
                },
                "to": [
                  {
                    "key_code": "left_arrow"
                  }
                ],
                "type": "basic"
              },
              {
                "from": {
                  "key_code": "k",
                  "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                  }
                },
                "to": [
                  {
                    "key_code": "down_arrow"
                  }
                ],
                "type": "basic"
              },
              {
                "from": {
                  "key_code": "l",
                  "modifiers": {
                    "mandatory": ["right_command"],
                    "optional": ["any"]
                  }
                },
                "to": [
                  {
                    "key_code": "right_arrow"
                  }
                ],
                "type": "basic"
              }
            ]
          }
        ]
      },
      "devices": [
        {
          "disable_built_in_keyboard_if_exists": false,
          "fn_function_keys": [],
          "identifiers": {
            "is_keyboard": true,
            "is_pointing_device": false,
            "product_id": 610,
            "vendor_id": 1452
          },
          "ignore": true,
          "manipulate_caps_lock_led": true,
          "simple_modifications": []
        },
        {
          "disable_built_in_keyboard_if_exists": false,
          "fn_function_keys": [],
          "identifiers": {
            "is_keyboard": true,
            "is_pointing_device": false,
            "product_id": 34050,
            "vendor_id": 2652
          },
          "ignore": false,
          "manipulate_caps_lock_led": false,
          "simple_modifications": [
            {
              "from": {
                "key_code": "application"
              },
              "to": {
                "key_code": "right_option"
              }
            },
            {
              "from": {
                "key_code": "caps_lock"
              },
              "to": {
                "key_code": "right_control"
              }
            },
            {
              "from": {
                "key_code": "end"
              },
              "to": {
                "key_code": "page_down"
              }
            },
            {
              "from": {
                "key_code": "home"
              },
              "to": {
                "key_code": "down_arrow"
              }
            },
            {
              "from": {
                "key_code": "insert"
              },
              "to": {
                "key_code": "left_arrow"
              }
            },
            {
              "from": {
                "key_code": "left_command"
              },
              "to": {
                "key_code": "left_option"
              }
            },
            {
              "from": {
                "key_code": "left_option"
              },
              "to": {
                "key_code": "left_command"
              }
            },
            {
              "from": {
                "key_code": "page_down"
              },
              "to": {
                "key_code": "page_up"
              }
            },
            {
              "from": {
                "key_code": "page_up"
              },
              "to": {
                "key_code": "right_arrow"
              }
            },
            {
              "from": {
                "key_code": "pause"
              },
              "to": {
                "key_code": "fn"
              }
            },
            {
              "from": {
                "key_code": "print_screen"
              },
              "to": {
                "key_code": "up_arrow"
              }
            },
            {
              "from": {
                "key_code": "right_option"
              },
              "to": {
                "key_code": "right_command"
              }
            },
            {
              "from": {
                "key_code": "scroll_lock"
              },
              "to": {
                "key_code": "fn"
              }
            }
          ]
        },
        {
          "disable_built_in_keyboard_if_exists": false,
          "fn_function_keys": [],
          "identifiers": {
            "is_keyboard": true,
            "is_pointing_device": false,
            "product_id": 630,
            "vendor_id": 1452
          },
          "ignore": false,
          "manipulate_caps_lock_led": true,
          "simple_modifications": [
            {
              "from": {
                "key_code": "caps_lock"
              },
              "to": {
                "key_code": "left_control"
              }
            }
          ]
        },
        {
          "disable_built_in_keyboard_if_exists": false,
          "fn_function_keys": [],
          "identifiers": {
            "is_keyboard": true,
            "is_pointing_device": true,
            "product_id": 544,
            "vendor_id": 1452
          },
          "ignore": false,
          "manipulate_caps_lock_led": true,
          "simple_modifications": []
        }
      ],
      "fn_function_keys": [
        {
          "from": {
            "key_code": "f1"
          },
          "to": {
            "consumer_key_code": "display_brightness_decrement"
          }
        },
        {
          "from": {
            "key_code": "f2"
          },
          "to": {
            "consumer_key_code": "display_brightness_increment"
          }
        },
        {
          "from": {
            "key_code": "f3"
          },
          "to": {
            "key_code": "mission_control"
          }
        },
        {
          "from": {
            "key_code": "f4"
          },
          "to": {
            "key_code": "launchpad"
          }
        },
        {
          "from": {
            "key_code": "f5"
          },
          "to": {
            "key_code": "illumination_decrement"
          }
        },
        {
          "from": {
            "key_code": "f6"
          },
          "to": {
            "key_code": "illumination_increment"
          }
        },
        {
          "from": {
            "key_code": "f7"
          },
          "to": {
            "consumer_key_code": "rewind"
          }
        },
        {
          "from": {
            "key_code": "f8"
          },
          "to": {
            "consumer_key_code": "play_or_pause"
          }
        },
        {
          "from": {
            "key_code": "f9"
          },
          "to": {
            "consumer_key_code": "fastforward"
          }
        },
        {
          "from": {
            "key_code": "f10"
          },
          "to": {
            "consumer_key_code": "mute"
          }
        },
        {
          "from": {
            "key_code": "f11"
          },
          "to": {
            "consumer_key_code": "volume_decrement"
          }
        },
        {
          "from": {
            "key_code": "f12"
          },
          "to": {
            "consumer_key_code": "volume_increment"
          }
        }
      ],
      "name": "Filco Minila Air",
      "parameters": {
        "delay_milliseconds_before_open_device": 1000
      },
      "selected": true,
      "simple_modifications": [
        {
          "from": {
            "key_code": "caps_lock"
          },
          "to": {
            "key_code": "left_control"
          }
        }
      ],
      "virtual_hid_keyboard": {
        "caps_lock_delay_milliseconds": 0,
        "country_code": 0,
        "keyboard_type": "ansi",
        "mouse_key_xy_scale": 100
      }
    }
  ]
}

```
