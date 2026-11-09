# Documentation Rewrite Case Study: Webhook Setup

This case study demonstrates my ability to audit complex, poorly structured developer documentation and rewrite it for clarity, conciseness, and improved user experience.

---

## The Original Text (Before)
*Below is the original documentation provided by the engineering team. It is wordy, lacks a clear sequence, and mixes prerequisites with actual steps.*

> **Configuring Webhook Endpoints in the Dashboard**
> To get events in your system you need webhooks. Users must go to the Developer Settings tab which is inside the main account dashboard and find the webhooks subsection. Before you do that, make sure your server can receive POST requests and that you have a destination URL that is public, because localhost won't work unless you use a tunneling tool like ngrok. When you are in the screen, click the add endpoint button. You will be asked for a URL payload. Put your URL there. You also have to choose which events you want us to send you. We recommend only selecting the ones you actually need so you don't overload your server capacity. Finally, there is a secret key generated automatically. You must save this signing secret because it is critical to verify that the signatures of the events coming to your server are actually from us and not a malicious third party. Click save when you are done.

---

## The Rewritten Version (After)
*Here is the optimized version. Information is separated into prerequisites, structured into logical numbered steps, and key security warnings are visually highlighted.*

### Webhook Integration Guide

Webhooks allow your application to receive real-time HTTP POST notifications when events occur in your account. 

### Prerequisites
Before configuring your webhook endpoint in the dashboard, ensure you have:
*   A publicly accessible server URL capable of receiving `POST` requests. 
*   *Note: For local development, use a tunneling tool such as [ngrok](https://ngrok.com) to generate a public URL.*

### Configuration Steps

1.  Log in to your account dashboard and navigate to **Developer Settings** > **Webhooks**.
2.  Click **Add Endpoint**.
3.  In the **Payload URL** field, enter your public server URL.
4.  Under **Event Selection**, select only the specific event types your system needs to process (e.g., `payment.success`, `user.created`). *Limiting events optimizes server performance.*
5.  Click **Save**.

### ⚠️ Critical Security Step: Verify Signatures
Upon saving, the system automatically generates a unique **Signing Secret** (`whsec_...`) for your endpoint. 

You must copy and store this secret safely in your server's environment variables. Use it to verify the cryptographic signatures of incoming payloads to ensure requests originate exclusively from our platform.

---

## Summary of Improvements
1.  **Readability:** Converted a dense wall of text into a scannable, step-by-step procedure.
2.  **Information Architecture:** Separated environmental prerequisites from the actionable steps.
3.  **Visual Hierarchy:** Used bolding for UI elements (e.g., **Add Endpoint**) and a dedicated callout block for the critical security warning, preventing users from missing the signing secret.
