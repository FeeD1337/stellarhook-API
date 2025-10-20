# StellarHook Lua API Documentation

This is documentation for the StellarHook Lua API, which allows you to interact with game entities, weapons, input commands, global variables, configuration variables, and rendering functions.

## Table of Contents

- [Script Management](#script-management)
- [Key Bindings](#key-bindings)
- [Configuration Variables](#configuration-variables)
- [Player Information](#player-information)
- [Player State and Movement](#Player-State-and-Movement)
- [Weapons](#weapons)
- [Drawing](#drawing)
- [Hooks](#Hooks)
- [ImGui Interface](#imgui-interface)
- [AutoWall Functions](#autowall-functions)
- [Aimbot Functions](#aimbot-functions)
- [Resolver Functions](#Resolver Functions)
- [Extended Player Functions](#extended-player-functions)
- [LagComp Functions](#lagcomp-functions)
- [Ray Tracing](#ray-tracing)
- [Prediction Functions](#Prediction-Functions)
- [Vector Functions](#vector-functions)
- [Time and Ticks](#time-and-ticks)
- [Other Functions](#other-functions)

## Script Management

### Script Control Functions
### register_tab(name)
Registers a new tab in the menu with the given name.

### register_menu_element()
Registers a custom menu element that will be rendered in the menu.

### add_tab_content(tab_name)
Adds content to the specified tab. The content is defined in a function named render_tab_<tab_name>.

### wait(seconds)
Pauses script execution for the specified number of seconds.

### is_in_game() -> boolean
Checks if the player is currently in a game.

### Binding Mode Constants

```lua
BIND_MODE_NONE   -- No binding mode
BIND_MODE_HOLD   -- Hold key mode
BIND_MODE_TOGGLE -- Toggle mode
```

## Key Bindings

### create_bind(name) -> bind_id
Creates a new key binding with the specified name.

### get_bind_state(bind_id) -> boolean
Returns the current state of the binding (active or not).

### set_bind_key(bind_id, key_code)
Sets the key for the binding.

### set_bind_mode(bind_id, mode)
Sets the binding mode (BIND_MODE_NONE, BIND_MODE_HOLD, BIND_MODE_TOGGLE).

### get_bind_key(bind_id) -> key_code
Returns the key code for the binding.

### get_bind_mode(bind_id) -> mode
Returns the binding mode.

### cheat_bind_exists(name) -> boolean
Checks if a bind with the specified name exists.

### cheat_create_bind(name, key, mode) -> boolean
Creates a new bind with the given name, key code, and mode (0=None, 1=Hold, 2=Toggle). Returns true on success.

### cheat_remove_bind(name) -> boolean
Removes the bind with the specified name. Returns true on success.

### cheat_set_bind_key(name, key) -> boolean
Sets the key for the bind with the given name. Returns true on success.

### cheat_set_bind_mode(name, mode) -> boolean
Sets the mode for the bind with the given name. Returns true on success.

### cheat_get_bind_key(name) -> key_code
Returns the key code for the bind with the given name.

### cheat_get_bind_mode(name) -> mode
Returns the mode for the bind with the given name.

### cheat_get_bind_state(name) -> boolean
Returns the current state (active or not) of the bind with the given name.

### cheat_get_all_binds() -> table
Returns a table of all available bind names.

## Configuration Variables

### create_bool(path, initial_value) -> boolean
Creates a new boolean configuration variable at the specified path with the initial value. Returns true on success.

### create_int(path, initial_value) -> boolean
Creates a new integer configuration variable at the specified path with the initial value. Returns true on success.

### create_float(path, initial_value) -> boolean
Creates a new float configuration variable at the specified path with the initial value. Returns true on success.

### create_color(path, r, g, b, a) -> boolean
Creates a new color configuration variable at the specified path with the initial color. Returns true on success.

### set_bool(cvar_path, value)
Sets a boolean value for a configuration variable.

### set_int(cvar_path, value)
Sets an integer value for a configuration variable.

### set_float(cvar_path, value)
Sets a floating-point value for a configuration variable.

### set_color(cvar_path, r, g, b, a)
Sets a color value for a configuration variable.

### get_bool(cvar_path) -> boolean
Returns the boolean value of a configuration variable.

### get_int(cvar_path) -> integer
Returns the integer value of a configuration variable.

### get_float(cvar_path) -> number
Returns the floating-point value of a configuration variable.

### get_color(cvar_path) -> r, g, b, a
Returns the color components of a configuration variable.

### list_cvars() -> table
Returns a table of all available configuration variables.

## Player Information

### player:is_alive() -> boolean
Checks if the player is alive.

### player:is_dormant() -> boolean
Checks if the player is dormant.

### player:get_eye_angles() -> pitch, yaw, roll
Returns the player's eye angles.

### player:set_eye_angles(pitch, yaw, roll)
Sets the player's eye angles.

### player:set_base_velocity(x, y, z)
Sets the player's base velocity.

### player:set_fall_velocity(velocity)
Sets the player's fall velocity.

### player:set_view_offset(x, y, z)
Sets the player's view offset.

### player:set_abs_velocity(x, y, z)
Sets the player's absolute velocity.

### player:set_punch_angle(x, y, z)
Sets the player's punch angle.

### player:get_abs_velocity() -> x, y, z
Returns the player's absolute velocity.

### get_local_player() -> player
Returns the local player object.

### get_player(index) -> player
Returns a player object by index.

### player:get_name() -> string
Returns the player's name.

### player:get_team() -> integer
Returns the player's team number.

### player:get_health() -> integer
Returns the player's health amount.

### player:get_origin() -> x, y, z
Returns the player's position coordinates.

### player:get_eye_position() -> x, y, z
Returns the player's eye position coordinates.

### player:get_velocity() -> x, y, z
Returns the player's velocity vector.

### player:get_weapon() -> weapon
Returns the player's current weapon.

### player:get_flags() -> integer
Returns the player's flags.

### player:get_armor() -> integer
Returns the player's armor amount.

### player:has_helmet() -> boolean
Checks if the player has a helmet.

### player:get_move_type() -> integer
Returns the player's movement type.

### player:get_simulation_time() -> number
Returns the player's simulation time.

## Player State and Movement

### get_velocity() -> number
Returns the local player's velocity magnitude.

### get_fall_velocity() -> number
Returns the local player's fall velocity.

### get_local_origin() -> x, y, z
Returns the local player's origin coordinates.

### get_punch_angle() -> x, y, z
Returns the local player's punch angle.

### get_view_offset() -> x, y, z
Returns the local player's view offset.

### get_base_velocity() -> x, y, z
Returns the local player's base velocity.

### get_fire_bullets_spread() -> number
Returns the fire bullets spread value.

### get_accuracy() -> number
Returns the local player's accuracy.

### get_eye_position() -> x, y, z
Returns the local player's eye position.

### is_in_air() -> boolean
Checks if the local player is in the air.

### get_thirdperson_angles() -> x, y, z
Returns the thirdperson angles.

### set_thirdperson_angles(x, y, z)
Sets the thirdperson angles.

### get_global_velocity(player_index) -> x, y, z
Returns the global velocity of the specified player.

## Weapons

### weapon:get_weapon_id() -> integer
Returns the weapon's ID.

### weapon:get_weapon_name() -> string
Returns the weapon's name.

### weapon:is_ready_to_shoot() -> boolean
Checks if the weapon is ready to shoot.

### weapon:is_in_reload() -> boolean
Checks if the weapon is currently reloading.

### weapon:get_clip1() -> integer
Returns the number of bullets in the primary magazine.

### weapon:get_clip2() -> integer
Returns the number of bullets in the secondary magazine.

### weapon:get_primary_ammo() -> integer
Returns the number of spare bullets for the primary weapon.

### weapon:get_secondary_ammo() -> integer
Returns the number of spare bullets for the secondary weapon.

### weapon:get_next_primary_attack() -> number
Returns the time until the next possible primary fire attack.

### weapon:get_next_secondary_attack() -> number
Returns the time until the next possible secondary fire attack.

## Drawing

### get_text_width(text) -> width
Returns the width of the text when drawn.

### world_to_screen(x, y, z) -> screen_x, screen_y, visible
Converts 3D world coordinates to 2D screen coordinates.

### draw_line(x1, y1, x2, y2, r, g, b, a)
Draws a line on the screen.

### draw_rect(x, y, w, h, r, g, b, a)
Draws a rectangle on the screen.

### draw_filled_rect(x, y, w, h, r, g, b, a)
Draws a filled rectangle on the screen.

### draw_circle(x, y, radius, segments, r, g, b, a)
Draws a circle on the screen.

### draw_filled_circle(x, y, radius, segments, r, g, b, a)
Draws a filled circle on the screen.

### draw_text(x, y, r, g, b, a, text)
Draws text on the screen.

### draw_gradient_h(x, y, w, h, r1, g1, b1, a1, r2, g2, b2, a2)
Draws a horizontal gradient on the screen.

### draw_gradient_v(x, y, w, h, r1, g1, b1, a1, r2, g2, b2, a2)
Draws a vertical gradient on the screen.

### draw_3d_box(x, y, z, width, height, depth, r, g, b, a) -> success
Draws a 3D box in world coordinates.

### draw_hitbox(entity_index, hitbox_id, r, g, b, a) -> success
Draws a hitbox of the specified entity.

### draw_skeleton(entity_index, r, g, b, a) -> success
Draws a skeleton of the specified entity.

## Hooks

### hook_vmt(interface_name_or_address, index, new_function) -> success
Hooks a virtual method table function. Returns true if successful.

### unhook_vmt(interface_name_or_address, index) -> success
Unhooks a virtual method table function. Returns true if successful.

### get_original_vmt(interface_name_or_address, index) -> original_function
Gets the original VMT function.

### hook_netvar(table_name, prop_name, new_proxy) -> success
Hooks a netvar proxy function. Returns true if successful.

### unhook_netvar(table_name, prop_name) -> success
Unhooks a netvar proxy function. Returns true if successful.

### get_original_netvar(table_name, prop_name) -> original_function
Gets the original netvar proxy function.

## ImGui Interface

### imgui_begin(title, flags) -> boolean
Begins a new ImGui window.

### imgui_end()
Ends the current ImGui window.

### imgui_begin_child(id, width, height, border, flags) -> boolean
Begins a child ImGui window.

### imgui_end_child()
Ends the child ImGui window.

### imgui_set_next_window_pos(x, y, condition, pivot_x, pivot_y)
Sets the position for the next ImGui window.

### imgui_set_next_window_size(width, height, condition)
Sets the size for the next ImGui window.

### imgui_text(text)
Displays text in ImGui.

### imgui_checkbox(label, cvar_path) -> changed, value
Displays a checkbox in ImGui.

### imgui_button(label, width, height) -> pressed
Displays a button in ImGui.

### imgui_slider_int(label, cvar_path, min, max) -> changed, value
Displays a slider for integers in ImGui.

### imgui_slider_float(label, cvar_path, min, max) -> changed, value
Displays a slider for floating-point numbers in ImGui.

### imgui_same_line(offset_from_start_x, spacing)
Places the next element on the same line.

### imgui_begin_window(title, flags) -> boolean
Begins a new ImGui window (alternative method).

### imgui_end_window()
Ends the current ImGui window (alternative method).

### imgui_set_window_pos(x, y, condition)
Sets the position of the current ImGui window.

### imgui_set_window_size(width, height, condition)
Sets the size of the current ImGui window.

### imgui_separator()
Adds a separator line in ImGui.

### imgui_begin_main_menu_bar() -> boolean
Begins the main menu bar in ImGui.

### imgui_end_main_menu_bar()
Ends the main menu bar in ImGui.

### imgui_begin_menu(label, enabled) -> boolean
Begins a submenu in ImGui.

### imgui_end_menu()
Ends a submenu in ImGui.

### imgui_menu_item(label, selected) -> activated, selected
Adds a menu item in ImGui.

### imgui_color_picker(label, cvar_path) -> changed
Adds a color picker in ImGui.

### imgui_combo(label, cvar_path, items) -> changed
Adds a dropdown list in ImGui.

### imgui_input_text(label, default_text, buf_size) -> changed, text
Adds a text input field in ImGui.

### imgui_get_async_key_state(vk_code) -> boolean
Checks the state of a key.

### imgui_push_style_var(idx, val)
Pushes a style variable onto the stack.

### imgui_pop_style_var(count)
Pops style variables from the stack.

### imgui_push_style_color(idx, r, g, b, a)
Pushes a style color onto the stack.

### imgui_pop_style_color(count)
Pops style colors from the stack.

### imgui_set_style_var(idx, val)
Sets a style variable directly.

### imgui_set_style_color(idx, r, g, b, a)
Sets a style color directly.

### imgui_set_window_font_scale(scale)
Sets the font scale for the current window.

### imgui_set_cursor_pos(x, y)
Sets the cursor position within the current window.

### imgui_get_window_size() -> width, height
Gets the current window size.

### imgui_get_window_pos() -> x, y
Gets the current window position.

### imgui_is_item_hovered() -> hovered
Returns true if the last item is hovered.

### imgui_is_item_clicked() -> clicked
Returns true if the last item was clicked.

### imgui_v_slider_float(label, width, height, value, min, max, format) -> value, changed
Adds a vertical slider for float values.

### imgui_v_slider_int(label, width, height, value, min, max, format) -> value, changed
Adds a vertical slider for integer values.

### imgui_input_text(label, default_text, buf_size) -> changed, text
Adds a text input field in ImGui.

### imgui_input_float(label, value, step, step_fast, format) -> value, changed
Adds an input field for float values.

### imgui_input_int(label, value, step, step_fast) -> value, changed
Adds an input field for integer values.

### imgui_tree_node(label) -> open
Creates a tree node that can be expanded.

### imgui_tree_push(id)
Pushes tree node state.

### imgui_tree_pop()
Pops tree node state.

### imgui_progress_bar(fraction, width, height, overlay)
Adds a progress bar.

### imgui_dummy(width, height)
Adds a dummy element for spacing.

### imgui_spacing()
Adds vertical spacing.

### imgui_new_line()
Adds a new line.

### imgui_plot_lines(label, values_table, overlay, min, max, width, height)
Plots an array of values as lines.

### imgui_plot_histogram(label, values_table, overlay, min, max, width, height)
Plots an array of values as a histogram.

### imgui_radio_button(label, active) -> clicked
Adds a radio button.

### imgui_selectable(label, selected) -> selected, clicked
Adds a selectable item.

### imgui_collapsing_header(label) -> open
Adds a collapsing header.

### imgui_list_box(label, current, items_table) -> current, changed
Adds a list box.

### imgui_menu_bar() -> has_menu
Starts a menu bar.

### imgui_menu_item(label, selected) -> result, selected
Adds a menu item.

### imgui_checkbox_flags(label, flags, flag_value) -> flags, changed
Adds a checkbox for bit flags.

### imgui_drag_float(label, value, speed, min, max, format) -> value, changed
Adds a draggable float control.

### imgui_drag_int(label, value, speed, min, max, format) -> value, changed
Adds a draggable integer control.

### imgui_color_edit3(label, r, g, b) -> r, g, b, changed
Adds a color editor for RGB values.

### imgui_color_edit4(label, r, g, b, a) -> r, g, b, a, changed
Adds a color editor for RGBA values.

### imgui_image(texture_id, width, height)
Displays an image.

### imgui_image_button(texture_id, width, height) -> clicked
Adds an image button.

### imgui_begin_tab_bar(id) -> open
Starts a tab bar.

### imgui_end_tab_bar()
Ends a tab bar.

### imgui_begin_tab_item(name) -> open
Starts a tab item.

### imgui_end_tab_item()
Ends a tab item.

### imgui_begin_table(id, columns) -> open
Starts a table.

### imgui_end_table()
Ends a table.

### imgui_table_next_row(min_height)
Moves to the next table row.

### imgui_table_set_column_index(column_index) -> success
Sets the current column index in a table.

### imgui_table_setup_column(label, init_width)
Sets up a table column.

### imgui_tooltip(text)
Adds a tooltip with the specified text.

### imgui_begin_tooltip()
Starts a tooltip window.

### imgui_end_tooltip()
Ends a tooltip window.

### imgui_begin_popup(id) -> open
Begins a popup window.

### imgui_end_popup()
Ends a popup window.

### imgui_open_popup(id)
Opens a popup by ID.

### imgui_close_current_popup()
Closes the currently open popup

### imgui_is_popup_open(id) -> open
Checks if a popup is currently open.

### imgui_begin_main_menu_bar() -> has_menu
Starts the main menu bar. Returns true if the menu bar is visible.

### imgui_end_main_menu_bar()
Ends the main menu bar.

### imgui_begin_menu(label, enabled) -> open
Starts a menu. Returns true if the menu is open.

### imgui_end_menu()
Ends a menu.

### imgui_menu_item(label, selected) -> clicked, selected
Adds a menu item. Returns whether it was clicked and its selected state.

### imgui_begin_tab_item(name) -> open
Starts a tab item. Returns true if the tab is open and active.

### imgui_end_tab_item()
Ends a tab item.

### imgui_begin_tab_bar(id) -> open
Starts a tab bar. Returns true if the tab bar is visible.

### imgui_end_tab_bar()
Ends a tab bar.

### imgui_columns(count, id, border)
Sets up columns in the current window.

### imgui_next_column()
Moves to the next column.

### imgui_set_column_width(column_index, width)
Sets the width of a specific column.

## AutoWall Functions

### autowall_can_hit(start_x, start_y, start_z, end_x, end_y, end_z, target_index) -> hit, damage
Checks if it's possible to hit through walls and returns potential damage.

### autowall_get_damage(start_x, start_y, start_z, end_x, end_y, end_z) -> damage
Calculates damage when hitting through walls.

## Aimbot Functions

### aimbot_get_best_hitbox(target_index) -> hitbox_id, pos_x, pos_y, pos_z
Finds the best hitbox for shooting at the specified target.

### aimbot_check_visible(start_x, start_y, start_z, end_x, end_y, end_z, target_index) -> visible
Checks visibility between two points considering the specified target.

### aimbot_get_hitbox_position(entity_index, hitbox_id) -> pos_x, pos_y, pos_z
Returns the position of the specified entity's hitbox.

## Resolver Functions

### set_resolver_override(function)
Sets a resolver override function.

### get_resolver_side(player_index) -> side
Gets the resolver side for a player.

### set_resolver_side(player_index, side)
Sets the resolver side for a player.

### get_resolver_data(player_index) -> data_table
Gets resolver data for a player.

## Extended Player Functions

### player_get_hitbox_position(player_index, hitbox_id) -> pos_x, pos_y, pos_z
Returns the position of the specified player's hitbox.

### player_get_bone_position(player_index, bone_id) -> pos_x, pos_y, pos_z
Returns the position of the specified player's bone.

### player_is_visible(player_index) -> visible
Checks if the specified player is visible from the local player's position.

## LagComp Functions

### lagcomp_get_records_count(player_index) -> count
Returns the number of lag compensation records for the specified player.

### lagcomp_get_record_position(player_index, record_index) -> pos_x, pos_y, pos_z
Returns the position of the specified lag compensation record.

### lagcomp_get_best_record(player_index) -> record_index
Returns the index of the best lag compensation record for the specified player.

## Ray Tracing

### trace_ray(start_x, start_y, start_z, end_x, end_y, end_z, mask) -> hit, fraction, entity_index
Performs ray tracing in the game world and returns the result.

## Prediction Functions

### start_prediction() -> boolean
Starts the prediction system. Returns true if successful.

### end_prediction() -> boolean
Ends the prediction system. Returns true if successful.

### run_simulation() -> boolean
Runs the simulation. Returns true if successful.

### predict_origin(entity_index) -> x, y, z
Predicts the origin of the specified entity.

### update_player_history(entity_index) -> boolean
Updates the player history for the specified entity. Returns true if successful.

### get_predicted_origin(entity_index, ping) -> x, y, z
Returns the predicted origin of the specified entity, adjusted for ping.

### get_player_history(entity_index) -> x, y, z
Returns the player history origin for the specified entity.

### is_prediction_data_valid() -> boolean
Checks if the prediction data is valid.

### get_prediction_vars() -> table
Returns a table containing prediction variables.

## Vector Functions

### vector_distance(x1, y1, z1, x2, y2, z2) -> distance
Calculates the distance between two points in 3D space.

### vector_angle(x, y, z) -> pitch, yaw
Converts a direction vector to angles (pitch and yaw).

### angle_vectors(pitch, yaw) -> dir_x, dir_y, dir_z
Converts angles to a direction vector.

### calc_angle(src_x, src_y, src_z, dst_x, dst_y, dst_z) -> pitch, yaw
Calculates angles between two points in 3D space.

## Time and Ticks

### get_tick_count() -> integer
Returns the current tick count.

### get_game_ticks() -> integer
Returns the number of game ticks.

### get_bullets_fired() -> integer
Returns the number of bullets fired.

### get_player_bullets_fired(player_index) -> integer
Returns the number of bullets fired by the specified player.

### get_simulation_time() -> number
Returns the current simulation time.

### get_anim_time() -> number
Returns the current animation time.

### time() -> number
Returns the current time in seconds.

### wait(seconds)
Pauses script execution for the specified number of seconds.

## Other Functions

### print(text)
Outputs text to the console.

### get_screen_size() -> width, height
Returns the screen dimensions.

### get_mouse_pos() -> x, y
Returns the current mouse cursor position.

### is_mouse_in(x, y, w, h) -> boolean
Checks if the mouse cursor is in the specified area.

### hsv_to_rgb(h, s, v) -> r, g, b
Converts color from HSV to RGB.

### rgb_to_hsv(r, g, b) -> h, s, v
Converts color from RGB to HSV.

### is_in_game() -> boolean
Checks if the player is in game.

### is_shifting() -> boolean
Checks if tick shifting is being performed.

### get_doubletap_charge() -> integer
Returns the double tap charge.

### get_ticks_to_shift() -> integer
Returns the number of ticks until shift.

## Usage Examples

### AutoWall Example

```lua
-- Check if it's possible to hit through a wall
local local_player = get_local_player()
local eye_pos = {local_player:get_eye_position()}
local target = get_player(1) -- Get the first player
local target_pos = {target:get_eye_position()}

local can_hit, damage = autowall_can_hit(
    eye_pos[1], eye_pos[2], eye_pos[3],
    target_pos[1], target_pos[2], target_pos[3],
    1
)

if can_hit then
    print("Can hit through wall! Damage: " .. damage)
else
    print("Cannot hit through wall")
end
```

### Aimbot Example

```lua
-- Get the best hitbox for shooting
local target_index = 1
local hitbox_id, pos_x, pos_y, pos_z = aimbot_get_best_hitbox(target_index)

if hitbox_id ~= -1 then
    print("Best hitbox: " .. hitbox_id)
    print("Position: " .. pos_x .. ", " .. pos_y .. ", " .. pos_z)
    
    -- Check hitbox visibility
    local local_player = get_local_player()
    local eye_pos = {local_player:get_eye_position()}
    
    local visible = aimbot_check_visible(
        eye_pos[1], eye_pos[2], eye_pos[3],
        pos_x, pos_y, pos_z,
        target_index
    )
    
    if visible then
        print("Hitbox is visible")
    else
        print("Hitbox is not visible")
    end
end
```

### Extended Drawing Example

```lua
-- Draw player skeleton
function on_paint()
    for i = 1, 64 do
        local player = get_player(i)
        if player and player:get_health() > 0 and player:get_team() ~= get_local_player():get_team() then
            draw_skeleton(i, 255, 0, 0, 255) -- Red skeleton for enemies
        end
    end
end

-- Draw 3D box around player
function on_paint()
    for i = 1, 64 do
        local player = get_player(i)
        if player and player:get_health() > 0 then
            local origin = {player:get_origin()}
            draw_3d_box(origin[1], origin[2], origin[3], 30, 72, 30, 0, 255, 0, 255)
        end
    end
end
```

### LagComp Example

```lua
-- Get positions from lag compensation records
function on_paint()
    local target_index = 1
    local records_count = lagcomp_get_records_count(target_index)
    
    if records_count > 0 then
        local best_record = lagcomp_get_best_record(target_index)
        local pos_x, pos_y, pos_z = lagcomp_get_record_position(target_index, best_record)
        
        -- Draw a point at the best record position
        local screen_x, screen_y, visible = world_to_screen(pos_x, pos_y, pos_z)
        if visible then
            draw_filled_circle(screen_x, screen_y, 5, 20, 255, 255, 0, 255)
        end
    end
end
```

### Ray Tracing Example

```lua
-- Ray tracing to check for obstacles
local local_player = get_local_player()
local eye_pos = {local_player:get_eye_position()}
local forward = {angle_vectors(get_view_offset())}
local end_pos = {
    eye_pos[1] + forward[1] * 1000,
    eye_pos[2] + forward[2] * 1000,
    eye_pos[3] + forward[3] * 1000
}

local hit, fraction, entity_index = trace_ray(
    eye_pos[1], eye_pos[2], eye_pos[3],
    end_pos[1], end_pos[2], end_pos[3],
    0x46004003 -- MASK_SHOT
)

if hit then
    print("Ray hit an obstacle at distance: " .. (fraction * 1000))
    if entity_index ~= -1 then
        print("Ray hit an entity with index: " .. entity_index)
    end
end
```

### Vector Functions Example

```lua
-- Calculate distance between players
local local_player = get_local_player()
local local_pos = {local_player:get_origin()}
local target = get_player(1)
local target_pos = {target:get_origin()}

local distance = vector_distance(
    local_pos[1], local_pos[2], local_pos[3],
    target_pos[1], target_pos[2], target_pos[3]
)

print("Distance to target: " .. distance)

-- Calculate angle for aiming
local pitch, yaw = calc_angle(
    local_pos[1], local_pos[2], local_pos[3],
    target_pos[1], target_pos[2], target_pos[3]
)

print("Aiming angle: " .. pitch .. ", " .. yaw)
```
