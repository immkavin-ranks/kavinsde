## Introduction

>Information security as “protecting information and information systems from unauthorized access, use, disclosure, disruption, modification, or destruction”

Four major aspects of information security:
- Integrity - guard against improper modification or destruction of the data and ensure non-repudiation and authenticity of information.
- Data confidentiality - prevent illegitimate access or disclosure of sensitive information.
- Availability - guarantee timely and reliable access to and use of information.
- Authentication - only legitimate and authorized users should be able to access the data and carry out specific tasks.

## Soft Biometrics 

There are many situations where primary biometric traits (i.e., face, fingerprint and iris) are either corrupted or unavailable, and the soft biometric information is the only available clue to solving a crime.

For example, while a surveillance video may not capture the complete face of a suspect, the face image in the video may reveal the suspect’s gender and ethnicity, or the presence of a mark or tattoo may provide additional valuable clues. 

We will discuss some of the soft biometric traits (i.e., periocular, facial marks, and tattoos) below. 

The periocular biometric is gaining increasing attention since it offers a trade-off between using the entire face image and the iris portion only. Facial marks and tattoos are also gaining widespread attention since they offer complementary information that can be exploited along with primary biometric traits.

### Periocular

The periocular region represents the region around the eyes.

 It predominantly consists of the skin, eyebrow, and eye. 

The use of the periocular region as a biometric cue represents a good trade-off between using the entire face region or using only the iris for recognition. 

When the entire face is imaged from a distance, the iris information is typically of low resolution; this means the matching performance due to the iris modality will be poor. 

On the other hand, when the iris is imaged at small standoff (typically, 1 meter), the entire face may not be available, thereby forcing the recognition system to rely only on the iris.

Periocular images can also be captured in the NIR spectrum to minimize illumination variation compared to visible spectrum.

Periocular images contain common components across images (i.e., iris, sclera, and eyelids) that can be represented in a common coordinate system. 

![](attachments/Pasted%20image%2020250213222337.png)
Figure: Example of periocular images from two different subjects.

![](attachments/Pasted%20image%2020250213224019.png)
Figure: Example images showing difficulties in periocular image alignment

![](attachments/Pasted%20image%2020250213224056.png)
Figure: Schematic of image alignment and feature extraction processes for periocular images.

### Face Marks

Advances in sensing technology have made it easy to capture high resolution face
images. From these high resolution face images, it is possible to extract details of
skin irregularities, also known as facial marks.

This has opened new possibilities in face representation and matching schemes. These skin details are mostly ignored and considered as noise in a typical face recognition system.

 However, facial marks can be used to 
 1. supplement existing facial matchers to improve the identification accuracy, 
 2. facilitate fast face image retrieval, 
 3. enable matching or retrieval with partial or off-frontal face images, and 
 4. provide more descriptive evidence about the similarity or dissimilarity between face images, which can be used as evidence in legal proceedings.

![](attachments/Pasted%20image%2020250213223816.png)

To represent the face marks in a common coordinate system, primary facial features such as eyes, eye brows, nose, mouth, and face boundary are detected by using an Active Appearance Model (AAM) or Active Shape Model (ASM).

![](attachments/Pasted%20image%2020250213224433.png)
Figure:  Schematic of the mark detection process.

### Tattoos 

When the primary biometric traits are unavailable or corrupted, tattoos can be used to identify victims or suspects.

Therefore, recognition of tattoos can provide a better understanding of an individuals background and membership in various organizations, especially criminal gangs.
