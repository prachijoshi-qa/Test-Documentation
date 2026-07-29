Application Name – Discord (High Level Test Cases & Its Priority) 
Type – Communication App  


1. Functional Test Cases  

Registration & Login & Forgot Password (P0) 
    • Check Registration with Phone Number & Email Both - Valid Data, Invalid Data , Empty Fields
    • Check Login with Email /Phone & Password  -  Valid Data, Invalid Data , Empty Fields
    • Test Login with FaceID & also when Security Key is Removed
    • Verify Forgot Password
Onboarding (P0) 
    • Check Onboarding Flow After Signup 

Messages (P0) 
    • Verify able to find & add friends
    • Verify Send Message , Voice Call & Video Call

Server & Channel Management: ( P0 )
    • Create  Servers, Channels , Create Roles & Add People 
    • Roles & Permissions: Verify that a "Moderator" role can delete messages while a "Member" role cannot.
    • Channel Visibility: Ensure private channels are strictly invisible to users without the specific role.
    • Threads: Test if a thread correctly archives after the set period of inactivity (24h, 3d, etc.).
    • Test Remove Servers ,Channels & People

Messaging & Rich Content: (P1)
    • Markdown Rendering: Verify that bold, *italics*, and `code` blocks render correctly across Desktop, Web, and Mobile.
    • File Limits: Attempt to upload a file exceeding the 10MB limit (or higher for Nitro users) and verify the error message.
    • Mentions: Ensure @everyone, @here, and role mentions trigger notifications only for the intended users.
Voice & Video (P1)
    • Noise Suppression: Test "Krisp" noise cancellation by introducing background noise (like a fan) during a call.
    • Stream Quality: Verify that "Go Live" screen sharing adjusts quality dynamically based on network bandwidth.
    • Test Screen Sharing in Call 

2. Security & Privacy Test Cases (P0)
    • Presence Masking:
        ◦ Invisible Status: Verify that an "Invisible" user does not appear in the presences array of the WebSocket API (to prevent "Invisible" detection leaks).
    • Authentication:
        ◦ MFA (Multi-Factor Authentication): Verify that login is blocked if the 2FA code is incorrect.
        ◦ Session Invalidation: Ensure that "Log out of all devices" successfully terminates active tokens on other platforms.
    • Data Privacy:
        ◦ Message Deletion: Verify that once a message is deleted, it is unreachable via direct API calls.
3. Cross-Platform & Compatibility
Discord runs on Electron (Desktop), React Native (Mobile), and standard Web browsers.
Platform	Specific Test Case
Desktop (P1)	Verify "Push-to-Talk" works even when the app is minimized/not in focus.
Mobile (P1)	Test "Handoff" — start a voice call on Desktop and switch to Mobile without disconnecting.
Web (P1)	Verify that the browser version supports "Screenshare" without requiring a plugin.
Hardware (P2)	Ensure the app detects hot-swapping audio devices (e.g., plugging in a USB headset during a call).
4. Performance & Edge Cases (P2)
    • High-Volume Servers: Test the UI lag in a server with 500,000+ members and constant message flow.
    • Offline Mode: Verify that messages sent while offline are queued and sent automatically once the connection is restored.
    • Bot Interactions: Use slash commands (e.g., /help) and verify that the "Interaction Failed" message doesn't appear under normal network conditions.

5. Veify Application Compatibility with Mobile (P2)

    • Test Battery Usage When Actively Using app & also When app is running in background
    • Check if Extra usage of app cause Mobile heating
    • Test Screen Rotation setting is working for app
    • Check Notification settings from phone also works for app
    • Check Allow/ Deny Permissions for Locations, Camera, Phone, photos, microphone works fine
    • Test  Uninstall , install again
    • Test Installation when No space
    • Test IOS & Android Both apps 
    • Test UI with  Differenr Screen size Phones or Simulators  (Ipad , Iphone 8-17, Android ) 




