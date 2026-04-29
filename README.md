# StellarHook Lua API Documentation

This documentation describes the Lua API for StellarHook

## Script Management
- `register_tab(name)`
- `register_menu_element()`
- `add_tab_content(tab_name)`
- `wait(seconds)`
- `is_in_game()`

## Key Bindings
- `create_bind(name)`
- `get_bind_state(name)`
- `set_bind_key(name, key_code)`
- `set_bind_mode(name, mode)`
- `get_bind_key(name)`
- `get_bind_mode(name)`
- `cheat_bind_exists(name)`
- `cheat_create_bind(name, key, mode)`
- `cheat_remove_bind(name)`
- `cheat_set_bind_key(name, key)`
- `cheat_set_bind_mode(name, mode)`
- `cheat_get_bind_key(name)`
- `cheat_get_bind_mode(name)`
- `cheat_get_bind_state(name)`
- `cheat_get_all_binds()`

## Configuration Variables
- `create_bool(path, initial_value)`
- `create_int(path, initial_value)`
- `create_float(path, initial_value)`
- `create_color(path, r, g, b, a)`
- `set_bool(cvar_path, value)`
- `set_int(cvar_path, value)`
- `set_float(cvar_path, value)`
- `set_color(cvar_path, r, g, b, a)`
- `get_bool(cvar_path)`
- `get_int(cvar_path)`
- `get_float(cvar_path)`
- `get_color(cvar_path)`
- `list_cvars()`
- `find_convar(name)`
- `convar_get_int(convar_name)`
- `convar_get_float(convar_name)`
- `convar_get_bool(convar_name)`
- `convar_set_int(convar_name, value)`
- `convar_set_float(convar_name, value)`
- `convar_set_bool(convar_name, value)`

## Player Information
- `get_local_player()`
- `get_player(index)`
- `player_get_name(index)`
- `player:is_alive()`
- `player:get_velocity()`
- `player:get_bullets_fired()`
- `player:has_defuser()`
- `player:get_sequence_activity(sequence)`
- `player:get_pose_parameter(index)`
- `player:set_pose_parameter(index, value)`
- `player:get_anim_overlay(index)`
- `player:get_num_anim_overlays()`
- `player:get_observer_target()`
- `player:get_observer_mode()`
- `player:get_max_health()`
- `player:is_dying()`
- `player:get_velocity_modifier()`
- `player:get_cycle()`
- `player:set_cycle(cycle)`
- `player:get_sequence()`
- `player:set_sequence(sequence)`
- `player:get_playback_rate()`
- `player:get_max_health_value()`
- `player:get_max_speed()`
- `player:get_water_level()`
- `player:is_ducked()`
- `player:in_duck_jump()`
- `player:get_duck_time()`
- `player:get_jump_time()`
- `player:get_duck_jump_time()`
- `player:get_collision_group()`
- `player:get_punch_angle_vel()`
- `player:invalidate_bone_cache()`
- `player:set_abs_origin(x, y, z)`
- `player:set_abs_angles(x, y, z)`
- `player:set_local_origin(x, y, z)`
- `player:set_local_angles(x, y, z)`
- `player:lookup_pose_parameter(name)`
- `player:weapon_get_slot(slot)`
- `player:is_scoped()`
- `player:get_render_color()`
- `player:is_ducking()`
- `player:is_in_air()`
- `player:is_spawn_protected()`
- `player:get_account()`
- `player:get_bonus_progress()`
- `player:is_dormant()`
- `player:get_eye_angles()`
- `player:set_eye_angles(pitch, yaw, roll)`
- `player:set_base_velocity(x, y, z)`
- `player:set_fall_velocity(velocity)`
- `player:set_view_offset(x, y, z)`
- `player:set_abs_velocity(x, y, z)`
- `player:set_punch_angle(x, y, z)`
- `player:get_abs_velocity()`
- `player:get_team()`
- `player:get_health()`
- `player:get_origin()`
- `player:get_eye_position()`
- `player:get_weapon()`
- `player:get_flags()`
- `player:get_armor()`
- `player:has_helmet()`
- `player:get_move_type()`
- `player:get_simulation_time()`

## Player State and Movement
- `get_velocity()`
- `get_fall_velocity()`
- `get_local_origin()`
- `get_punch_angle()`
- `get_view_offset()`
- `get_base_velocity()`
- `get_fire_bullets_spread()`
- `get_accuracy()`
- `get_eye_position()`
- `is_in_air()`
- `get_thirdperson_angles()`
- `set_thirdperson_angles(x, y, z)`
- `get_global_velocity(player_index)`

## Weapons
- `weapon:get_weapon_id()`
- `weapon:get_weapon_name()`
- `weapon:is_ready_to_shoot()`
- `weapon:is_in_reload()`
- `weapon:get_clip1()`
- `weapon:get_clip2()`
- `weapon:get_primary_ammo()`
- `weapon:get_secondary_ammo()`
- `weapon:get_next_primary_attack()`
- `weapon:get_next_secondary_attack()`

## Drawing
- `get_text_width(text)`
- `world_to_screen(x, y, z)`
- `draw_line(x1, y1, x2, y2, r, g, b, a)`
- `draw_rect(x, y, w, h, r, g, b, a)`
- `draw_filled_rect(x, y, w, h, r, g, b, a)`
- `draw_circle(x, y, radius, r, g, b, a)`
- `draw_filled_circle(x, y, radius, r, g, b, a)`
- `draw_text(x, y, text, r, g, b, a)`
- `draw_gradient_h(x, y, w, h, r1, g1, b1, a1, r2, g2, b2, a2)`
- `draw_gradient_v(x, y, w, h, r1, g1, b1, a1, r2, g2, b2, a2)`
- `draw_3d_box(x, y, z, width, height, depth, r, g, b, a)`
- `draw_hitbox(entity_index, hitbox_id, r, g, b, a)`
- `draw_skeleton(entity_index, r, g, b, a)`

## Hooks
- `hook_vmt(interface_name_or_address, index, new_function)`
- `unhook_vmt(interface_name_or_address, index)`
- `get_original_vmt(interface_name_or_address, index)`
- `hook_netvar(table_name, prop_name, new_proxy)`
- `unhook_netvar(table_name, prop_name)`
- `get_original_netvar(table_name, prop_name)`
- `pattern_scan(module_name, signature)`
- `get_module_base(module_name)`

## ImGui Interface
- `imgui_begin(title, flags) -> boolean`
- `imgui_end()`
- `imgui_begin_child(id, width, height, border, flags) -> boolean`
- `imgui_end_child()`
- `imgui_set_next_window_pos(x, y, condition, pivot_x, pivot_y)`
- `imgui_set_next_window_size(width, height, condition)`
- `imgui_text(text)`
- `imgui_checkbox(label, cvar_path) -> changed, value`
- `imgui_button(label, width, height) -> pressed`
- `imgui_slider_int(label, cvar_path, min, max) -> changed, value`
- `imgui_slider_float(label, cvar_path, min, max) -> changed, value`
- `imgui_same_line(offset_from_start_x, spacing)`
- `imgui_begin_window(title, flags) -> boolean`
- `imgui_end_window()`
- `imgui_set_window_pos(x, y, condition)`
- `imgui_set_window_size(width, height, condition)`
- `imgui_separator()`
- `imgui_begin_main_menu_bar() -> boolean`
- `imgui_end_main_menu_bar()`
- `imgui_begin_menu(label, enabled) -> boolean`
- `imgui_end_menu()`
- `imgui_menu_item(label, selected) -> activated, selected`
- `imgui_color_picker(label, cvar_path) -> changed`
- `imgui_combo(label, cvar_path, items) -> changed`
- `imgui_input_text(label, default_text, buf_size) -> changed, text`
- `imgui_get_async_key_state(vk_code) -> boolean`
- `imgui_push_style_var(idx, val)`
- `imgui_pop_style_var(count)`
- `imgui_push_style_color(idx, r, g, b, a)`
- `imgui_pop_style_color(count)`
- `imgui_set_style_var(idx, val)`
- `imgui_set_style_color(idx, r, g, b, a)`
- `imgui_set_window_font_scale(scale)`
- `imgui_set_cursor_pos(x, y)`
- `imgui_get_window_size() -> width, height`
- `imgui_get_window_pos() -> x, y`
- `imgui_is_item_hovered() -> hovered`
- `imgui_is_item_clicked() -> clicked`
- `imgui_v_slider_float(label, width, height, value, min, max, format) -> value, changed`
- `imgui_v_slider_int(label, width, height, value, min, max, format) -> value, changed`
- `imgui_input_text(label, default_text, buf_size) -> changed, text`
- `imgui_input_float(label, value, step, step_fast, format) -> value, changed`
- `imgui_input_int(label, value, step, step_fast) -> value, changed`
- `imgui_tree_node(label) -> open`
- `imgui_tree_push(id)`
- `imgui_tree_pop()`
- `imgui_progress_bar(fraction, width, height, overlay)`
- `imgui_dummy(width, height)`
- `imgui_spacing()`
- `imgui_new_line()`
- `imgui_plot_lines(label, values_table, overlay, min, max, width, height)`
- `imgui_plot_histogram(label, values_table, overlay, min, max, width, height)`
- `imgui_radio_button(label, active) -> clicked`
- `imgui_selectable(label, selected) -> selected, clicked`
- `imgui_collapsing_header(label) -> open`
- `imgui_list_box(label, current, items_table) -> current, changed`
- `imgui_menu_bar() -> has_menu`
- `imgui_menu_item(label, selected) -> result, selected`
- `imgui_checkbox_flags(label, flags, flag_value) -> flags, changed`
- `imgui_drag_float(label, value, speed, min, max, format) -> value, changed`
- `imgui_drag_int(label, value, speed, min, max, format) -> value, changed`
- `imgui_color_edit3(label, r, g, b) -> r, g, b, changed`
- `imgui_color_edit4(label, r, g, b, a) -> r, g, b, a, changed`
- `imgui_image(texture_id, width, height)`
- `imgui_image_button(texture_id, width, height) -> clicked`
- `imgui_begin_tab_bar(id) -> open`
- `imgui_end_tab_bar()`
- `imgui_begin_tab_item(name) -> open`
- `imgui_end_tab_item()`
- `imgui_begin_table(id, columns) -> open`
- `imgui_end_table()`
- `imgui_table_next_row(min_height)`
- `imgui_table_set_column_index(column_index) -> success`
- `imgui_table_setup_column(label, init_width)`
- `imgui_tooltip(text)`
- `imgui_begin_tooltip()`
- `imgui_end_tooltip()`
- `imgui_begin_popup(id) -> open`
- `imgui_end_popup()`
- `imgui_open_popup(id)`
- `imgui_close_current_popup()`
- `imgui_is_popup_open(id) -> open`
- `imgui_begin_main_menu_bar() -> has_menu`
- `imgui_end_main_menu_bar()`
- `imgui_begin_menu(label, enabled) -> open`
- `imgui_end_menu()`
- `imgui_menu_item(label, selected) -> clicked, selected`
- `imgui_begin_tab_item(name) -> open`
- `imgui_end_tab_item()`
- `imgui_begin_tab_bar(id) -> open`
- `imgui_end_tab_bar()`
- `imgui_columns(count, id, border)`
- `imgui_next_column()`
- `imgui_set_column_width(column_index, width)`

## AutoWall Functions
- `autowall_can_hit(start_x, start_y, start_z, end_x, end_y, end_z, target_index)`
- `autowall_get_damage(start_x, start_y, start_z, end_x, end_y, end_z)`
- `autowall_on_totaldamage(callback)`
- `autowall_on_canhitwithautowall(callback)`

## Aimbot Functions
- `aimbot_get_best_hitbox(target_index)`
- `aimbot_check_visible(start_x, start_y, start_z, end_x, end_y, end_z, target_index)`
- `aimbot_get_hitbox_position(entity_index, hitbox_id)`

## Resolver Functions
- `set_resolver_override(function)`

## Extended Player Functions
- `player_get_hitbox_position(player_index, hitbox_id)`
- `player_get_bone_position(player_index, bone_id)`
- `player_is_visible(player_index)`

## LagComp Functions
- `lagcomp_get_records_count(player_index)`
- `lagcomp_get_record_position(player_index, record_index)`
- `lagcomp_get_best_record(player_index)`
- `lagcomp_on_backtrack_restore(callback)`
- `lagcomp_on_select(callback)`
- `lagcomp_on_backtrack_apply(callback)`

## Ray Tracing
- `trace_ray(start_x, start_y, start_z, end_x, end_y, end_z)`

## Prediction Functions
- `start_prediction()`
- `end_prediction()`
- `run_simulation()`
- `predict_origin(entity_index)`
- `update_player_history(entity_index)`
- `get_predicted_origin(entity_index, ping)`
- `get_player_history(entity_index)`
- `is_prediction_data_valid()`
- `get_prediction_vars()`

## Vector Functions
- `vector_distance(x1, y1, z1, x2, y2, z2)`
- `vector_angle(x, y, z)`
- `angle_vectors(pitch, yaw, roll)`
- `calc_angle(src_x, src_y, src_z, dst_x, dst_y, dst_z)`
- `hsv_to_rgb(h, s, v)`
- `rgb_to_hsv(r, g, b)`

## Time and Ticks
- `get_tick_count()`
- `get_game_ticks()`
- `get_bullets_fired()`
- `get_player_bullets_fired(player_index)`
- `get_simulation_time(player_index)`
- `get_anim_time(player_index)`
- `time()`

## Other Functions
- `print(text)`
- `get_screen_size()`
- `get_mouse_pos()`
- `is_mouse_in(x, y, w, h)`
- `is_shifting()`
- `get_doubletap_charge()`
- `get_ticks_to_shift()`

## Logging Functions
- `log_message(message)`
- `log_warning(message)`
- `log_error(message)`
- `set_log_filter(filter)`
- `get_log_filter()`

## AnimFix Functions
- `animfix_on_update(callback)`
- `animfix_on_updatelocalplayer(callback)`
- `animfix_on_forcefeetyaw(callback)`
- `animfix_on_getcurrentfeetyaw(callback)`
- `animfix_on_getgoalfeetyaw(callback)`

## GameEvent Functions
- `register_event(event_name, callback)`
- `unregister_event(event_name, callback_ref)`

## CallBack Functions
- `framestagenotify(callback to FSN)`
- `createmove(callback to CREATEMOVE)`

