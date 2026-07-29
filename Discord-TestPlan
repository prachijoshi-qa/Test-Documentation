 Quality Assurance Test Plan: Discord

1. Document Control & Strategy
    • Version: 2026.3.1
    • Target Environments:
        ◦ Desktop: Windows 11 / macOS Sonoma (Electron Build)
        ◦ Mobile: iOS 19 / Android 14 (React Native Architecture)
        ◦ Web: Chrome 140+ / Safari 19+ (WebRTC Engine)
    • Approach: Risk-based automation for regression and manual exploratory testing for media/hardware handoffs.
2. Test Scope & Exclusions 
In-Scope (High Priority Core Pillars)
    • Authentication & Onboarding: Registration, Single Sign-On (SSO), and Secure Multi-Factor Authentication (2FA) lifecycle.
    • Text & Rich Media Processing: Text formatting rendering, markdown validation, and image/attachment uploading.
    • Real-time Communication (VoIP): Direct voice/video infrastructure connectivity and streaming latency.
    • Cross-Device Continuity: Synchronized sessions, system configuration hooks, and context transfers.
Out-of-Scope
    • Internal server performance testing of backend infrastructure (to be handled exclusively by the Core Infrastructure DevOps/SRE teams).
    • Payment gateway validation for localized currency providers outside North America.
3. Prioritized Test Cases (P0 to P2)
Phase 1: Smoke & Critical Path Testing (P0)
If any of these scenarios fail, the release build is instantly rejected.
TC-P0-01: Onboarding, Account Creation & Authentication
    • Objective: Validate that new users can join and that existing users can recover access securely.
    • Steps:
        1. Submit a registration form with unique email strings.
        2. Trigger the "Forgot Password" option from the login card.
        3. Use the generated email reset token to successfully update credentials.
        4. Attempt to reuse that exact link a second time.
    • Expected Result: Accounts are generated successfully. Password resets force an immediate invalidation of all existing active sessions on other devices, and duplicate use of a single reset token returns a safe "Link Expired" response.

TC-P0-02: Core Text Messaging & Permission Control
    • Objective: Verify instant text delivery and strict channel permission enforcement.
    • Steps:
        1. Send core messages utilizing formatting parameters (**bold**, *italics*, `code blocks`).
        2. Restrict channel access via Server Roles (e.g., removing a member's view permission for a private text channel).
        3. Attempt to fetch private channel indices using a restricted User Token.
    • Expected Result: Formatting displays correctly. Denied channels instantly disappear from the client sidebar layout and return hard 403 Forbidden statuses if targeted via raw API requests.
TC-P0-03: Audio & Video VoIP Stream Pipeline
    • Objective: Verify realtime audio and video capture functionality.
    • Steps:
        1. Connect a client to a target Voice Channel. 
        2. Toggle webcam streaming and screen capture pipelines simultaneously.
    • Expected Result: Media connects seamlessly without dropping frames or triggering RTC connection tracking faults.
Phase 2: System Continuity & Integration (P1)
Major feature validation ensuring a smooth across-device experience.
TC-P1-01: Cross-Platform Voice Call Handoff
    • Objective: Transfer active calls dynamically between devices.
    • Steps:
        1. Join an active voice call via the Desktop client.
        2. Launch the Mobile app using the same account and tap the active green call banner.
        3. Choose to transition audio routing to the phone.
    • Expected Result: The media stream shifts to the mobile hardware layers smoothly without disconnecting the underlying channel connection or dropping participants.
TC-P1-02: Desktop Push-to-Talk (PTT) App Backgrounding
    • Objective: Verify global OS keybind tracking when minimized.
    • Steps:
        1. Map a system-level keybind for Push-to-Talk (PTT) inside user preferences.
        2. Minimize the desktop client and run a resource-intensive game or application full-screen.
        3. Engage the keybind and talk.
    • Expected Result: The desktop background architecture hooks capture the OS input triggers correctly and pass audio packets continuously.
Phase 3: Compatibility & Edge Cases (P2)
Validating environmental variances, layout issues, and system boundaries.
TC-P2-01: Peripheral Audio Hot-Swapping
    • Objective: Verify client stability during direct hardware modifications.
    • Steps:
        1. Disconnect an active USB or Bluetooth headset mid-call.
        2. Wait 3 seconds, reconnect the hardware piece, and re-engage.
    • Expected Result: The app engine catches the hardware removal gracefully without crashing the UI window thread and remaps the output lines to a device profile option smoothly.
TC-P2-02: Web Client Pluginless Screensharing
    • Objective: Verify web standard streaming without extra software extensions.
    • Steps:
        1. Access the web client via standard Google Chrome or Apple Safari browsers.
        2. Join a room and share a standalone browser tab.
    • Expected Result: Native WebRTC captures the target viewport successfully without prompting the user for external software downloads or app plug-ins.
4. Boundary, Negative & Crash Mitigation Test Matrix
Target Surface	Input Condition / Negative Action	System Level Validation	Expected Recovery Behavior
Sanitization Engine	Inject JS keywords (constructor, __proto__) into text elements.	String parser verification.	Treats strings as safe, literal text objects; does not execute code.
Object Lifecycles	Open a thread where the primary author account was deleted.	Null data lookup validation.	The user card displays cleanly as "Deleted User" rather than throwing a null pointer crash.
Network Boundaries	Drop network adapters completely mid-transit while chatting.	Queue tracking stability.	Text components turn gray to visually signal an offline state, queuing the payloads to send instantly upon re-connection.
5. Entry & Exit Benchmarks
Entry Criteria
    • Pre-production staging environments are fully operational.
    • All required API definitions are deployed to testing sandboxes.
    • Automated smoke testing regression frameworks are configured.

Exit Criteria
    • 100% of defined P0 Test Cases executed and marked as Passed. 
    • Open P1 functional defects = 0.
    • Remaining P2 bugs must have documented system workarounds
