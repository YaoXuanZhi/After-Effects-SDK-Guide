## PF_INDATA

&#160;&#160;&#160;&#160;&#160;&#160;
After Effects communicates system, project, layer and audio information using `PF_InData`. This structure is updated before each command selector is sent to a plug-in. Fields valid only during specific `PF_Cmds` are noted. Also, don’t worry; although `PF_InData` is dauntingly large, you need not memorize each member’s purpose; you’ll use some of the fields some of the time.

### Table 5: PF_INDATA

| **Name** | **Description** |
| :--- | :--- |
|**inter**|Callbacks used for user interaction, adding parameters, checking whether the user has interrupted the effect, displaying a progress bar, and obtaining source frames and parameter values at times other than the current time being rendered. This very useful function suite is described in `Interaction Callback Functions`.|
|**utils**|Graphical and mathematical callbacks. This pointer is defined at all times.|
|**effect_ref**|Opaque data that must be passed to most of the various callback routines. After Effects uses this to identify your plug-in.|
|**quality**|The current quality setting, either `PF_Quality_HI` or `PF_Quality_LO`. Effects should perform faster in LO, and more accurately in HI. The graphics utility callbacks perform differently between LO and HI quality; so should your effect! This field is defined during all frame and sequence selectors.|
|**version**|Effects specification version, Indicate the version you need to run successfully during `PF_Cmd_GLOBAL_SETUP`.|
|**serial_num**|The serial number of the invoking application.|
|**appl_id**|The identifier of the invoking application. If your plug-in is running in After Effects, `appl_id` contains the application creator code ‘`FXTC`’. Use this to test whether your plug-in, licensed for use with one application, is being used with another.|
|**num_params**|Input parameter count.|
|**what_cpu**|Under Mac OS this contains the Gestalt value for CPU type (see Inside Macintosh, volume 6). Undefined on Windows.|
|**what_fpu**|Under Mac OS this contains the Gestalt value for FPU type. Undefined on Windows.|
|**qd_globals**|With the advent of Carbon and Mac OS X, the use of this field is deprecated; it was a pointer to a read-only copy of the QuickDraw globals. It has always been undefined on Windows, and is now NULL on Mac OS as well.|
|**current_time**|The time of the current frame being rendered, valid during `PF_Cmd_RENDER`. This is the current time in the layer, not in any composition. If a layer starts at other than time 0 or is time-stretched, layer time and composition time are distinct.<br>The current frame number is `current_time` divided by `time_step`. The current time in seconds is `current_time` divided by `time_scale`.<br>To handle time stretching, composition frame rate changes, and time remapping, After Effects may ask effects to render at non-integral times (between two frames). Be prepared for this; don’t assume that you’ll only be asked for frames on frame boundaries. NOTE: As of CS3 (8.0), effects may be asked to render at negative current times. Deal!|
|**time_step**|The duration of the current source frame being rendered. In several situations with nested compositions, this source frame duration may be different than the time span between frames in the layer (`local_time_step`). This value can be converted to seconds by dividing by `time_scale`.<br>When calculating other source frame times, such as for `PF_CHECKOUT_PARAM`, use this value rather than `local_time_step`.<br>Can be negative if the layer is time-reversed. Can vary from one frame to the next if time remapping is applied on a nested composition.<br>Can differ from `local_time_step` when source material is stretched or remapped in a nested composition. For example, this could occur when an inner composition is nested within an outer composition with a different frame rate, or time remapping is applied to the outer composition.<br>This value will be 0 during `PF_Cmd_SEQUENCE_SETUP` if it is not constant for all frames. It will be set correctly during `PF_Cmd_FRAME_SETUP` and `PF_Cmd_FRAME_SETDOWN` selectors. WARNING: This can be zero, so check it before you divide.|
|**total_time**|Duration of the layer. If the layer is time-stretched longer than 100%, the value will be adjusted accordingly; but if the layer is time-stretched shorter, the value will not be affected. If time remapping is enabled, this value will be the duration of the composition. This value can be converted to seconds by dividing by `time_scale`.|
|**local_time_step**|Time difference between frames in the layer. Affected by any time stretch applied to a layer. Can be negative if the layer is time-reversed. Unlike `time_step`, this value is constant from one frame to the next. This value can be converted to seconds by dividing by `time_scale`.
For a step value that is constant over the entire frame range of the layer, use `local_time_step`, which is based on the composition’s framerate and layer stretch.|
|**time_scale**||
|**field**||
|**shutter_angle**||
|**width**||
|**height**||
|**extent_hint**||
|**output_origin_x**||
|**output_origin_y**||
|**downsample_x**||
|**downsample_y**||
|**pixel_aspect_ratio**||
|**in_flags**||
|**global_data**||
|**sequence_data**||
|**frame_data**||
|**start_sampL**||
|**dur_sampL**||
|**total_sampL**||
|**src_snd**||
|**pica_basicP**||
|**pre_effect_source_origin_x**||
|**pre_effect_source_origin_y**||
|**shutter_phase**||