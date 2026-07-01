# Live Mode

Live creates timestamped cues from a video, tab, window, or shared screen. The purpose is to understand the story without constantly watching and to reuse that story as transcript, dataset, or generation material.

## Start Live analysis

1. Open the video or screen you want to follow.
2. Open BonzAI+ → Live.
3. Choose the analysis mode and scene timing.
4. Select **Start Live Analysis**.
5. Grant the browser's screen/tab permission and select the correct source.

The model prepares transparently when needed. Status text explains capture, frame selection, analysis, validation, and waiting.

## Analysis modes

- **Fast:** fewer selected story frames and lower latency; best default for modest hardware.
- **Normal:** balanced context and responsiveness.
- **Quality:** richer frame evidence and slower output.

Scene window and wait settings affect how frames are grouped. Faster action benefits from denser raw sampling inside a meaningful scene window, not merely shorter captions.

## What Live tracks

BonzAI+ detects broad domains and adapts to subtypes. Examples include sports, fishing, gaming, combat, interviews, news, tutorials, cooking, travel, performances, film/action, product demonstrations, education, and general video.

It looks for visible subjects, actions, scene changes, speech/text cues, tools, locations, objectives, score/state, and subtype-specific highlights. A football goal, tennis break, caught fish, FPS frag, knockout, key quote, recipe step, or product reveal require different evidence.

## Timestamps

Entry timestamps come from the source video's playback time when available, not simply wall-clock capture time. They are intended to act as real editing or dataset cues.

## Transcript controls

- Remove an individual entry with the × control.
- Clear the entire transcript when analysis is stopped.
- Save the transcript for later use.
- Choose **Imagine** on an entry to use its caption as an image-generation prompt.

Stopping Live releases the old capture target. Starting again binds to the screen or video you currently select.

## Limits

Live is local and hardware-sensitive. A small realtime vision model can miss events or misread overlays. BonzAI uses multi-frame evidence, domain profiles, state tracking, repetition guards, and contradiction checks, but important transcripts should still be reviewed before publication or training.
