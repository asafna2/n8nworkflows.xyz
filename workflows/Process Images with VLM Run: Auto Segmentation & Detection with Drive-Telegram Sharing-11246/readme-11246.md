Process Images with VLM Run: Auto Segmentation & Detection with Drive-Telegram Sharing

https://n8nworkflows.xyz/workflows/process-images-with-vlm-run--auto-segmentation---detection-with-drive-telegram-sharing-11246


# Process Images with VLM Run: Auto Segmentation & Detection with Drive-Telegram Sharing

### 1. Workflow Overview

This workflow automates the processing and sharing of uploaded image files by leveraging VLM Run agents for image segmentation and object detection. It is designed to handle user-uploaded data, trigger parallel AI-powered processing, retrieve results via webhooks, extract secured download URLs, and distribute the processed images across multiple platforms for easy access and review.

**Target Use Cases:**  
- Automated image segmentation and object detection in medical or research images.  
- Seamless distribution of processed images to Google Drive and Telegram for collaboration or notification.  
- Handling files uploaded via a web form with support for PDF and CSV formats (adaptable to images).

**Logical Blocks:**

- **1.1 Input Reception:** User uploads file through a form trigger node.  
- **1.2 Parallel AI Processing:** The uploaded file is sent simultaneously to two VLM Run agents—one for segmentation and one for detection.  
- **1.3 Webhook Result Capture:** Two webhook nodes receive asynchronous callbacks with processing results from each agent.  
- **1.4 URL Extraction & Download:** A Code node extracts full signed Google Cloud Storage URLs, followed by an HTTP Request node that downloads the processed images using these URLs.  
- **1.5 Distribution:** The downloaded images are uploaded to Google Drive and sent to a Telegram chat for sharing.

---

### 2. Block-by-Block Analysis

#### 2.1 Input Reception

- **Overview:**  
  Captures user file uploads via a web-accessible form, initiating the workflow with the uploaded data.

- **Nodes Involved:**  
  - Upload Image

- **Node Details:**

  - **Upload Image**  
    - Type: Form Trigger  
    - Role: Entry point for user-submitted files; triggers workflow on form submission.  
    - Configuration:  
      - Form titled "Upload your data to test RAG".  
      - One required file input field accepting `.pdf` and `.csv` files.  
    - Input: External user submission.  
    - Output: Binary data of the uploaded file for downstream processing.  
    - Edge Cases:  
      - File type outside allowed extensions will be rejected by form.  
      - Large files or network interruptions could cause timeouts or incomplete uploads.

#### 2.2 Parallel AI Processing

- **Overview:**  
  Processes the uploaded file via two VLM Run agents concurrently: one performing image segmentation, the other object detection.

- **Nodes Involved:**  
  - VLM Run (Segmentation)  
  - VLM Run (Detection)

- **Node Details:**

  - **VLM Run (Segmentation)**  
    - Type: VLM Run Agent Node  
    - Role: Sends the uploaded file to the segmentation agent requesting segmented object images.  
    - Configuration:  
      - Operation: Execute agent.  
      - Agent prompt instructs segmentation of all objects and generation of segmented images, requesting only the completed download URL.  
      - Callback URL points to `/image_segmentation` webhook.  
    - Credentials: VLM Run API credentials with agent access.  
    - Input: Binary data from Upload Image node.  
    - Output: Asynchronous webhook call with segmentation results.  
    - Edge Cases:  
      - Agent API failures, network issues, or invalid input could cause processing errors.  
      - The prompt must remain precise to ensure proper URL response.

  - **VLM Run (Detection)**  
    - Type: VLM Run Agent Node  
    - Role: Sends the uploaded file to the detection agent requesting bounding box images.  
    - Configuration:  
      - Operation: Execute agent.  
      - Agent prompt instructs detection of all objects and generation of tight bounding box images, requesting only the completed download URL.  
      - Callback URL points to `/image_detection` webhook.  
    - Credentials: Same VLM Run API credentials as segmentation node.  
    - Input: Binary data from Upload Image node.  
    - Output: Asynchronous webhook call with detection results.  
    - Edge Cases: Similar to segmentation node.

#### 2.3 Webhook Result Capture

- **Overview:**  
  Two webhook nodes listen for asynchronous POST callbacks from VLM Run agents, capturing the URLs of processed images.

- **Nodes Involved:**  
  - Webhook for Segmented Image  
  - Webhook for Detected Image

- **Node Details:**

  - **Webhook for Segmented Image**  
    - Type: Webhook  
    - Role: Receives segmentation agent’s callback with signed URL payload.  
    - Configuration:  
      - HTTP Method: POST  
      - Path: `/image_segmentation`  
    - Output: JSON payload containing the signed URL.  
    - Edge Cases:  
      - Delayed or missing callbacks may cause workflow stalls.  
      - Payload format changes require regex update downstream.

  - **Webhook for Detected Image**  
    - Type: Webhook  
    - Role: Receives detection agent’s callback with signed URL payload.  
    - Configuration:  
      - HTTP Method: POST  
      - Path: `/image_detection`  
    - Output: JSON payload containing the signed URL.  
    - Edge Cases: Same as segmentation webhook.

#### 2.4 URL Extraction & Download

- **Overview:**  
  Extracts the full signed Google Cloud Storage URL from webhook payloads, then downloads the processed images securely.

- **Nodes Involved:**  
  - Code  
  - Download Image

- **Node Details:**

  - **Code**  
    - Type: Code (JavaScript)  
    - Role: Parses the webhook JSON payload text to extract the entire signed URL, including query parameters.  
    - Configuration:  
      - Uses regex `(https?:\/\/[^\s"]+)` to locate the URL in the JSON string.  
      - Returns extracted URL as JSON `{ url: fullSignedUrl }`.  
    - Input: JSON from webhook nodes.  
    - Output: JSON with extracted URL for image download.  
    - Edge Cases:  
      - Regex failure if URL format changes.  
      - Null or missing URL in payload results in download errors.

  - **Download Image**  
    - Type: HTTP Request  
    - Role: Downloads the image from the extracted signed URL.  
    - Configuration:  
      - URL parameterized to the extracted `url` from Code node.  
      - Uses default HTTP GET with no special options.  
    - Input: JSON with `url` field.  
    - Output: Binary image data.  
    - Edge Cases:  
      - Expired or invalid signed URLs cause download failure.  
      - Network timeouts or HTTP errors.

#### 2.5 Distribution

- **Overview:**  
  Shares the downloaded images by uploading them to Google Drive and sending them via Telegram.

- **Nodes Involved:**  
  - Upload File  
  - Send Image

- **Node Details:**

  - **Upload File**  
    - Type: Google Drive  
    - Role: Uploads the downloaded image to a specified Google Drive folder.  
    - Configuration:  
      - Target drive: "My Drive"  
      - Folder ID: `1S6baavqJn98MjUlbB6KtmARCWuWEekIZ` (configured folder)  
      - File name: Preset as "Patient Info" (could be dynamic in extended version)  
    - Credentials: Google Drive OAuth2 with upload permissions.  
    - Input: Binary image data from Download Image.  
    - Output: Google Drive file metadata.  
    - Edge Cases:  
      - OAuth token expiration or permission errors.  
      - Folder ID invalid or inaccessible.

  - **Send Image**  
    - Type: Telegram  
    - Role: Sends the downloaded image as a document to a Telegram chat.  
    - Configuration:  
      - Chat ID: `1872183963` (target Telegram chat)  
      - Operation: sendDocument with binary data enabled.  
    - Credentials: Telegram Bot API token with send message rights.  
    - Input: Binary image data from Download Image.  
    - Output: Telegram message metadata.  
    - Edge Cases:  
      - Invalid chat ID or bot token.  
      - Telegram API rate limits or downtime.

---

### 3. Summary Table

| Node Name                 | Node Type                     | Functional Role                                          | Input Node(s)                     | Output Node(s)                  | Sticky Note                                                                                                         |
|---------------------------|-------------------------------|----------------------------------------------------------|----------------------------------|--------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Upload Image              | Form Trigger                  | Accepts file upload to trigger workflow                  | External user                   | VLM Run (Segmentation), VLM Run (Detection) |                                                                                                                     |
| VLM Run (Segmentation)    | VLM Run Agent                 | Sends file to segmentation AI agent                      | Upload Image                    | Webhook for Segmented Image     |                                                                                                                     |
| VLM Run (Detection)       | VLM Run Agent                 | Sends file to detection AI agent                         | Upload Image                    | Webhook for Detected Image      |                                                                                                                     |
| Webhook for Segmented Image | Webhook                      | Receives segmentation results from AI                    | VLM Run (Segmentation) via callback | Code                          |                                                                                                                     |
| Webhook for Detected Image | Webhook                      | Receives detection results from AI                        | VLM Run (Detection) via callback | Code                          |                                                                                                                     |
| Code                      | Code                         | Extracts full signed URL from webhook JSON                | Webhook for Segmented Image, Webhook for Detected Image | Download Image                | # 🟥 Code Node & Image Download: Extract URL with regex, ensure full URL with query params for valid downloads       |
| Download Image            | HTTP Request                 | Downloads image from signed URL                            | Code                           | Send Image, Upload File          |                                                                                                                     |
| Upload File               | Google Drive                 | Uploads downloaded image to Google Drive folder           | Download Image                 | None                           | # 🟩 Upload to Drive & Send via Telegram: Requires Google Drive OAuth2 with upload permission                        |
| Send Image                | Telegram                     | Sends downloaded image as a Telegram document             | Download Image                 | None                           | # 🟩 Upload to Drive & Send via Telegram: Requires Telegram Bot token and chat ID correctly configured               |
| Sticky Note               | Sticky Note                  | Explains high-level workflow overview                      | None                          | None                           | # 🧠 Image Segmentation & Object Detection: Overview and logical flow description                                    |
| Sticky Note1              | Sticky Note                  | Explains VLM Run agents and webhook asynchronous pattern  | None                          | None                           | # 🟤 VLM Run Agents & Webhooks: Parallel processing and webhook callbacks                                           |
| Sticky Note2              | Sticky Note                  | Explains Code node regex extraction and image download    | None                          | None                           | # 🟥 Code Node & Image Download: Regex importance and download security notes                                        |
| Sticky Note3              | Sticky Note                  | Explains upload and Telegram sharing                       | None                          | None                           | # 🟩 Upload to Drive & Send via Telegram: Multi-channel sharing details                                             |
| Sticky Note4              | Sticky Note                  | Empty                                                      | None                          | None                           |                                                                                                                     |

---

### 4. Reproducing the Workflow from Scratch

1. **Create Form Trigger Node (Upload Image):**  
   - Type: Form Trigger  
   - Title: "Upload your data to test RAG"  
   - Add one form field:  
     - Type: File upload  
     - Label: "data"  
     - Required: Yes  
     - Accepted file types: `.pdf, .csv`  
   - This node will be the starting point triggered by form submission.

2. **Add Two VLM Run Agent Nodes:**  
   - **Segmentation Agent:**  
     - Type: VLM Run node (from @vlm-run/n8n-nodes-vlmrun package)  
     - Operation: Execute agent  
     - Agent Prompt: "Segment all objects from the given input and generate segmented image. Gve only completed url of the generated segmented image for download."  
     - Agent Callback URL: `https://playground.vlm.run/webhook/image_segmentation`  
     - Credentials: Provide VLM Run API credentials with agent access.  
     - Connect Output from "Upload Image" node to this node.  
   - **Detection Agent:**  
     - Same as above, but:  
     - Agent Prompt: "Detect all objects from the given input and generate tight bounding box image. Gve only completed url of the generated image for download."  
     - Agent Callback URL: `https://playground.vlm.run/webhook/image_detection`  
     - Connect Output from "Upload Image" node to this node.

3. **Create Two Webhook Nodes:**  
   - **Webhook for Segmented Image:**  
     - Type: Webhook  
     - HTTP Method: POST  
     - Path: `/image_segmentation`  
     - No authentication required (adjust if needed).  
     - This node listens for segmentation results.  
   - **Webhook for Detected Image:**  
     - Same as above, but Path: `/image_detection`  
     - Listens for detection results.

4. **Add a Code Node to Extract Signed URLs:**  
   - Type: Code  
   - Language: JavaScript  
   - Code snippet:  
     ```javascript
     return $input.all().map(item => {
       const text = JSON.stringify(item.json);
       const regex = /(https?:\/\/[^\s"]+)/;
       const match = text.match(regex);
       const fullSignedUrl = match ? match[0] : null;
       return { json: { url: fullSignedUrl } };
     });
     ```  
   - Connect outputs from both webhook nodes to this Code node.

5. **Add an HTTP Request Node to Download Images:**  
   - Type: HTTP Request  
   - Method: GET (default)  
   - URL: Use expression `{{$json["url"]}}` to dynamically set URL from Code node output.  
   - No authentication needed because URLs are signed.  
   - Connect Code node output to this node.

6. **Add Google Drive Node to Upload Downloaded Images:**  
   - Type: Google Drive  
   - Operation: Upload File  
   - Drive: My Drive (or your choice)  
   - Folder ID: Provide the Google Drive folder ID where files will be stored (e.g., `1S6baavqJn98MjUlbB6KtmARCWuWEekIZ`)  
   - Credentials: Google Drive OAuth2 with upload permission.  
   - Connect output of HTTP Request (Download Image) node to this node.

7. **Add Telegram Node to Send Images:**  
   - Type: Telegram  
   - Operation: sendDocument  
   - Chat ID: Target Telegram chat ID (e.g., `1872183963`)  
   - Enable sending binary data (file content).  
   - Credentials: Telegram Bot API token with message sending permissions.  
   - Connect output of HTTP Request (Download Image) node to this node.

8. **Connect Nodes Properly:**  
   - Upload Image → VLM Run (Segmentation) and VLM Run (Detection) in parallel.  
   - VLM Run agents trigger asynchronous callbacks to their respective webhook nodes.  
   - Both Webhook nodes → Code node (merge outputs).  
   - Code node → Download Image (HTTP Request).  
   - Download Image → Upload File (Google Drive) and Send Image (Telegram).

9. **Test Setup:**  
   - Ensure credentials are valid and have necessary permissions.  
   - Test file upload via form.  
   - Confirm VLM Run agents process input and callback webhooks fire.  
   - Confirm images download correctly and upload/send steps complete without errors.

---

### 5. General Notes & Resources

| Note Content                                                                                                                                                                  | Context or Link                                                                                                          |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| The workflow enables simultaneous asynchronous image segmentation and detection with VLM Run agents, enhancing processing efficiency.                                        | Sticky Note1                                                                                                           |
| Regex in the Code node must be maintained if VLM Run API changes the output format or URL structure for signed URLs.                                                         | Sticky Note2                                                                                                           |
| Google Drive and Telegram integrations require proper OAuth2 and API token configurations respectively, with necessary access rights for file upload and message sending.    | Sticky Note3                                                                                                           |
| The workflow includes detailed sticky notes explaining each major step for easier maintenance and understanding by future developers or automation agents.                   | Sticky Notes throughout the workflow                                                                                    |
| VLM Run platform and credentials are required to run agent nodes; ensure API keys are kept secure and usage limits are respected.                                            | VLM Run API documentation: https://docs.vlm.run/                                                                        |
| Telegram Bot setup instructions and Google Drive API setup guides are recommended to prepare credentials correctly.                                                          | Telegram Bot docs: https://core.telegram.org/bots/api, Google Drive API docs: https://developers.google.com/drive       |

---

**Disclaimer:** The provided text originates exclusively from an automated workflow created with n8n, a tool for integration and automation. This processing strictly complies with current content policies and contains no illegal, offensive, or protected elements. All manipulated data are legal and public.