# StellarHook Lua API Documentation

This is documentation for the StellarHook Lua API, which allows you to interact with game entities, weapons, input commands, global variables, configuration variables, and rendering functions.

## Table of Contents

- [Script Management](#script-management)
- [Key Bindings](#key-bindings)
- [Configuration Variables](#configuration-variables)
- [Player Information](#player-information)
- [Weapons](#weapons)
- [Drawing](#drawing)
- [ImGui Interface](#imgui-interface)
- [AutoWall Functions](#autowall-functions)
- [Aimbot Functions](#aimbot-functions)
- [Extended Player Functions](#extended-player-functions)
- [LagComp Functions](#lagcomp-functions)
- [Ray Tracing](#ray-tracing)
- [Vector Functions](#vector-functions)
- [Time and Ticks](#time-and-ticks)
- [Other Functions](#other-functions)

## Script Management

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

## Configuration Variables

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

## Weapons

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
