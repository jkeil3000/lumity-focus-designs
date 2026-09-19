# Developer handoff

## Product loop

1. The user grants Screen Time access.
2. The user selects individual apps and optionally groups them under a shared limit.
3. Opening a blocked app shows Apple's shield.
4. The shield opens Lumity Focus while preserving the identity of the triggering app.
5. The user chooses one of seven directions or selects Surprise me.
6. Lumity Focus presents one passage, video, or direct action.
7. The user either returns to their day or unlocks only the triggering app for the configured session.

There is no separate completion screen between the content and those two primary outcomes. A video excerpt may also offer a lower-emphasis `Continue watching here` action that resumes the same source inside Lumity Focus.

## Required v1 behavior

- Light appearance by default; Dark appearance is available.
- Individual and grouped app limits support minutes per open and a total daily allowance.
- Completing an interruption unlocks only the triggering app.
- Grouped apps share a daily allowance, while the requested app receives the temporary unlock.
- The interface shows successful opens today and remaining access.
- Content shuffles without replacement within each category and avoids an immediate repeat between cycles.
- Surprise me uses the same category queues.
- Reflections are optional, saved explicitly, and stored locally with their source content.
- No account, feed, streak, content browser, mandatory writing, or mandatory countdown.

## Content behavior

The categories are Spiritual, Philosophical, Entrepreneur, Creative, Reset, Relationships, and Movement.

Reading content must be copied verbatim from the attributed external source. It must include creator, work, edition or publisher when relevant, and a source URL. Lumity does not write or insert explanatory passages around the excerpt.

Reset, Relationships, and Movement each use ten finite direct instructions from the live content catalog. Present the instruction itself with an optional accessibility alternative. Do not transform an instruction into a multi-step coaching sequence.

Entrepreneur targets fifteen text passages and fifteen 60–120 second video clips. Use an official embed when available and provide a link to the complete source.

## YouTube excerpt behavior

- Store the YouTube video ID, `startSeconds`, `endSeconds`, creator, title, and complete source URL with each selected excerpt.
- Play the selected window through the official YouTube IFrame Player API. Do not download, screen-record, edit, or re-upload the source video.
- Keep the standard YouTube player, branding, controls, captions, advertisements, and links intact.
- When the selected window reaches `endSeconds`, treat the excerpt as finished and show the two primary Lumity outcomes outside the player.
- Also show a visually secondary `Continue watching here` action. It reloads the same video from `endSeconds` without another end boundary, so the user can watch the remainder inside Lumity Focus without entering YouTube's home feed or search experience.
- Continuing the full source does not unlock or consume time from the originally requested blocked app. The two primary Lumity outcomes remain available when the user stops or finishes watching.
- Keep a separate `View full source on YouTube` link for attribution and user choice. If embedding is unavailable, use that link as the fallback.

## Native feasibility gates

Before implementing the full interface, build a small iOS proof for:

1. Receiving the triggering app token from a shield action and opening the controlling app.
2. Unlocking only that app while other selected apps remain shielded.
3. Enforcing a ten-minute wall-clock session across backgrounding, force quit, reboot, and overlapping sessions.
4. Persisting per-app and group usage through an App Group without resetting usage when apps are regrouped.
5. Confirming the Family Controls entitlement and extension setup required for distribution.

Apple's documented 15-minute minimum DeviceActivity monitoring interval means a ten-minute session must be validated with a supported mechanism before the app architecture is treated as settled.

## Prototype limitations

The HTML prototype is a visual and interaction specification. Its counters and blockers are simulated in browser memory. Home copy remains editable, and the content catalog is still being curated.
