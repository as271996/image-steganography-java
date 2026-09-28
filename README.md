# Image Steganography

A Java desktop application that demonstrates image steganography using the Least Significant Bit (LSB) technique.

The application allows users to hide text data inside an image by modifying the least significant bits of the image bytes and later extract the hidden message from the generated image.

This project was developed as the core steganography technique later used in the Secure Data Transmission application.

## Features

- Load an image through a Java Swing desktop interface
- Hide text data inside an image using Least Significant Bit (LSB) steganography
- Extract hidden text from a steganographic image
- Store the hidden message length inside the image for accurate extraction
- Read message content from a text file before embedding
- Save the generated steganographic image as a PNG file
- Preview the selected image inside the application
- Reset the application state and process another image/message

## How It Works

The application uses the Least Significant Bit (LSB) steganography technique to hide text inside an image.

### Encoding

1. The user selects an image.
2. The text message is converted into bytes.
3. The application stores the message length inside the image.
4. Each message bit is written into the least significant bit of the image byte data.
5. The modified image is saved as a PNG file.

### Decoding

1. The steganographic image is loaded.
2. The stored message length is extracted first.
3. The application reads the least significant bits from the image bytes.
4. The extracted bits are reconstructed into the original text message.

Because only the least-significant bits of the image data are modified, the resulting visual changes are typically imperceptible under normal viewing conditions.

## Steganography vs Encryption

Steganography and encryption solve different problems.

- **Steganography** attempts to hide the existence of information.
- **Encryption** protects the contents of information even if it is discovered.

This project implements LSB steganography but does not currently provide cryptographic confidentiality. A stronger implementation could encrypt the message first and then embed the encrypted data into the image.

## Tech Stack

**Language:** Java 8  
**Desktop UI:** Java Swing  
**Image Processing:** BufferedImage, ImageIO  
**Core Technique:** Least Significant Bit (LSB) Steganography  
**Build / IDE:** NetBeans, Ant

## Project Structure

```text
Image-Steganography/
├── src/
│   └── image_steganography/
│       ├── ImageSteganography.java
│       ├── Encode.java
│       ├── Decode.java
│       └── ...
│
├── build.xml
├── manifest.mf
└── nbproject/
```

## Running the Application

### Prerequisites

Make sure the following are installed:

- Java 8 or later
- NetBeans IDE or another Java IDE with Ant support

### 1. Clone the Repository

```bash
git clone https://github.com/as271996/image-steganography-java.git
cd image-steganography-java
```

### 2. Open the Project

Open the project in NetBeans or another Java IDE that supports Ant-based projects.

### 3. Build the Project

Using Ant:

```bash
ant clean
ant
```

### 4. Run the Application

Run the main Java class from the IDE.

The application will launch as a Java Swing desktop interface where you can select an image, hide a text message inside it, and later extract the hidden message.

## Limitations and Future Improvements

This project demonstrates the core LSB steganography technique and can be further improved with:

- Validation to ensure the selected image has enough capacity for the message
- Support for additional image formats
- Improved error handling for invalid or unsupported files
- Secure password/key-based access for hidden messages
- Encryption of the message before embedding it into the image
- Improved Swing UI and user feedback
- Unit tests for encoding and decoding logic
- Clear separation between UI and steganography logic
- Support for hiding binary files in addition to text

## Author

**Amit Singh**

This project demonstrates the core image-steganography technique used as a foundation for the more complete Secure Data Transmission application.

- GitHub: [github.com/as271996](https://github.com/as271996)
- LinkedIn: [linkedin.com/in/amit-singh-sp27](https://www.linkedin.com/in/amit-singh-sp27)

## Limitations and Future Improvements

This project focuses on demonstrating the basic Least Significant Bit (LSB) steganography technique. It is intended as an educational implementation rather than a production-grade secure communication system.

### Current Limitations

- The hidden message is not encrypted before being embedded
- Anyone who knows the encoding technique could potentially extract the hidden data
- The application currently focuses on hiding text rather than arbitrary binary files
- Image capacity is limited by the number of available pixels / bytes
- Lossy image transformations or compression may destroy embedded data
- Error handling and input validation can be improved
- The UI and steganography logic are closely coupled

### Security Improvements

- Encrypt the message before embedding it into the image
- Add password/key-based encryption using a standard cryptographic algorithm such as AES
- Add integrity verification so modified or corrupted hidden messages can be detected
- Derive encryption keys securely from user-provided passwords
- Avoid relying on steganography alone for confidentiality

### Steganography Improvements

- Validate image capacity before attempting to encode a message
- Support hiding arbitrary binary files in addition to text
- Support additional lossless image formats where appropriate
- Randomize or pseudo-randomize the pixel positions used for embedding
- Allow configurable numbers of least-significant bits to be used
- Add metadata/version information to support future encoding formats
- Detect malformed or unsupported steganographic images during decoding

### Architecture & Code Quality

- Separate the Swing UI from the encoding/decoding logic
- Introduce dedicated services for image encoding and decoding
- Add custom exceptions and centralized error handling
- Improve validation for files, message sizes, and unsupported image formats
- Migrate the build from Ant to Maven or Gradle
- Upgrade to a modern Java LTS version

### Testing

- Add unit tests for message encoding and decoding
- Verify that encoded messages can be decoded without data loss
- Add boundary tests for maximum image capacity
- Add tests for empty messages and invalid input
- Add tests for corrupted or modified images
- Compare original and generated images to verify that only expected image data changes

### User Experience

- Display image capacity and message-size information before encoding
- Add file-selection validation and clearer error messages
- Show encoding/decoding progress for larger files
- Add drag-and-drop support
- Modernize the desktop interface
