#Can a Machine Learning Model Identify an Ill Baby?#

##Under Five Triage using Image and Pulse (U5-TIP)##


###Introduction###

Advanced paediatric life support is often needed because earlier danger signs of a life-threatening illness were not recognized.
Triage systems were developed to identify ill patients in emergencies and either shorten waiting times or lead to immediate resuscitation.
A triage system may use signs and symptoms like breathing, pulse, oxygen saturation, hydration, lethargy, vomiting everything and convulsions.(1,7)
Implementation of these triage systems are not always optimal and inexperienced health workers may find them complicated.(2)
An experienced health worker can often recognize an acutely ill baby immediately without doing triage.
Can a machine learning model be trained using images to recognize an ill baby that needs urgent attention? This will allow emergency care practioners
in ambulances and health workers at busy emergency departments to identify ill babies that need immediate attention.
In the literature machine learning triage models predicting admission to hospital or intensive care could be identified.(3–7) No models using images were found.
This work was done as part of the fastai machine learning course under the leadership of Jeremy Howard.(9)


###Method###

Images

Images of babies were collected with Google, Bing and DuckDuckGo using search words babies, infants, babies AND ill, babies AND dehydrated, 
babies AND septicemia, babies AND meningitis. Images were classified in 4 categories: Happy, Sad, Sleeping or Ill. Color images of all races were included. 
The majority of the images were from babies less than two years. Images of ill babies were the most difficult to find and only 22 images qualified for inclusion. 
Images containing any extras that could identify medical intervention were excluded. Between 22–26 images were selected for each category. An equivalent number 
of images in each category were downloaded to create a balanced dataset. Although many different strategies were used the best accuracy delivered by the model 
was 75%. The small dataset was the most likely contributor to the low accuracy. In an attempt to improve accuracy it was decided to use the face only. 
Face recognition programs were investigated but it could only identify the face in 50% of the images. Face recognition programs are trained on adult faces 
and not all the images were frontal. This may explain why there was difficulty in recognizing the faces. Images was then edited by using the photo edit function 
of a local machine. Faces were cropped to approximately 80% of the image size. Each image was copied and flipped to increase the size of the dataset.
The model was then trained with a convolutional neural network on a virtual machine with a GPU. (P-5000, 30 GB RAM, Paperspace Gradient)

Pulse

Pulse (heartbeat/min) was then added to improve the classification. A pulse approximately three standard deviations from the mean was used when the image was predicted as Ill, to classify a baby for immediate and urgent attention.
A study from O’Leary et al from Australia was used to define the centiles.(8)


###Results###

The best accuracy of 94.7% (range 78–95) for the image dataset was achieved with a ResNet101 architecture after 7 epochs with a learning rate of 3e-4. 
Densenet121 gave an accuracy of 92.1% after 16 epochs with a similar learning rate.


###Discussion###

In this model pulse was added with an algorithm when the image was classified as ill. In future with a larger dataset it may be possible to combine a 
vision neural network with a tabular neural network. Different or extra triage parameters may be proven in future to yield better results. With a large dataset 
of ill babies needing urgent attention triage may be done in future with an image only.

U5-TIP is a proof of concept even with a very small dataset of 96 images. Cropping, copying and flipping the images was an effective strategy to 
enlarge the dataset and improve accuracy.

Different models may be necessary for older children and adults. Pulse is also less sensitive in older children and adults to identify acute illness. 
Even for this model the age cut off at 5 years may be too high.

The next step would be the do a formal study in a medical setting to compare U5-TIP with existing triage models.

Future studies can then also be used to improve and increase the dataset on images for ill babies.


###Ethical Considerations###

Although images were collected from the public domain they were used without the parents permission. The images were anonymized and kept on a virtual 
and a private machine with security measures in place. Any future studies in this field using images of ill babies presenting at emergency departments 
will need the approval of ethical committees and consent of the parents. The implementation of any models developed will need to happen under medical supervision.


###References###

1.Cheema B, Twomey M. In: Health Do, editor. The South Africa Triage Scale (SATS), Training Manual 2012: Emergency Medicine Society of South Africa. 
Cape Town: Western Cape Government Department of Health; 2012. 
https://emssa.org.za/wp-content/uploads/2011/04/SATS-Manual-A5-LR-spreads.pdf.

2.Mould-Millman, NK., Dixon, J.M., Burkholder, T. et al. Validity and reliability of the South African Triage Scale in prehospital providers. 
BMC Emerg Med 21, 8 (2021). 
https://doi.org/10.1186/s12873-021-00406-6

This study was the first assessment of validity and inter-rater reliability of prehospital SATS triage among a cohort of South African Emergency Medical Services 
(EMS) providers. Overall, SATS under-performed as a prehospital triage tool. The study found good reliability, but poor validity, among EMS providers using SATS 
for prehospital triage in clinical vignettes. The final SATS triage color was correctly determined in only about one-half of cases. The under-triage rate of 30% 
was higher than previous reports from the in-hospital setting. The over-triage rate of 13% was acceptable. The high under-triage rate of SATS is attributable 
to under-calculation of the Triage Early Warning Score(TEWS) and incorrect use of clinical discriminators. Discriminators could be better tailored to prehospital 
medicine. Additional clinical and qualitative studies of EMS providers are needed to fully understand the performance and use of SATS.

3.Hong WS, Haimovich AD, Taylor RA (2018) Predicting hospital admission at emergency department triage using machine learning. 
PLoS ONE 13(7): e0201016. 
https://doi.org/10.1371/journal.pone.0201016

Machine learning can robustly predict hospital admission using triage information and patient history. The addition of historical information improves 
predictive performance significantly compared to using triage information alone, highlighting the need to incorporate these variables into prediction models.

4.Raita, Y., Goto, T., Faridi, M.K. et al. Emergency department triage prediction of clinical outcomes using machine learning models. 
Crit Care 23, 64 (2019). 
https://doi.org/10.1186/s13054-019-2351-7

Compared to the conventional approach, the machine learning models demonstrated a superior performance to predict critical care and hospitalization outcomes. 
The application of modern machine learning models may enhance clinicians’ triage decision making, thereby achieving better clinical care and optimal resource 
utilization.

5.Miles, J., Turner, J., Jacques, R. et al. Using machine-learning risk prediction models to triage the acuity of undifferentiated patients entering the 
emergency care system: a systematic review. 
Diagn Progn Res 4, 16 (2020). 
https://doi.org/10.1186/s41512-020-00084-1

There was a total of 92 models (from 25 studies) included in the review. There were two main triage outcomes: hospitalisation (56 models), and critical care 
need (25 models). For hospitalisation, neural networks and tree-based methods both had a median C-statistic of 0.81 (IQR 0.80–0.84, 0.79–0.82). 
Logistic regression had a median C-statistic of 0.80 (0.74–0.83). For critical care need, neural networks had a median C-statistic of 0.89 (0.86–0.91), 
tree based 0.85 (0.84–0.88), and logistic regression 0.83 (0.79–0.84).

6.Goto T, Camargo CA, Faridi MK, Freishtat RJ, Hasegawa K. Machine Learning–Based Prediction of Clinical Outcomes for Children During Emergency Department Triage.
JAMA Netw Open. 2019;2(1):e186937. 
https://jamanetwork.com/journals/jamanetworkopen/fullarticle/2720586

Machine learning–based triage had better discrimination ability to predict clinical outcomes and disposition, with reduction in undertriaging critically 
ill children and overtriaging children who are less ill.

7.Kwizera, Arthur MD1; Kissoon, Niranjan MD, PhD2; Musa, Ndidiamaka MD3; Urayeneza, Olivier MD, FACS4,5; Mujyarugamba, Pierre MSc4; Patterson, Andrew J. MD, 
PhD6; Harmon, Lori RRT, MBA7; Farmer, Joseph C. MD, FCCM8; Dünser, Martin W. MD9; Meier, Jens MD9; 
for the “Sepsis in Resource-Limited Nations” Task Force of the Surviving Sepsis Campaign A Machine Learning-Based Triage Tool for Children With Acute Infection 
in a Low Resource Setting*, 
Pediatric Critical Care Medicine: December 2019 — Volume 20 — Issue 12 — p e524-e530 
https://journals.lww.com/pccmjournal/Abstract/2019/12000/A_Machine_Learning_Based_Triage_Tool_for_Children.29.aspx

A machine learning-based algorithm could reliably predict hospital mortality in a Sub-Sahara African population of 949 children with an acute infection 
using easily collected information at admission which includes age, respiratory rate, capillary refill time, and altered mental state. 
Future studies need to evaluate and strengthen this algorithm in larger pediatric populations, both in high- and low-/middle-income countries.

8.O’Leary F, Hayen A, Lockie F, et al. 
Arch Dis Child 2015;100:733–737. 
http://dx.doi.org/10.1136/archdischild-2014-307401

Defining normal ranges and centiles for heart and respiratory rates in infants and children: a cross- sectional study of 668 616 patients attending an 
Australian tertiary hospital paediatric emergency department 1995–2011.

9.Jeremy Howard, Sylvain Gugger. Information 2020, 11(2), 108. fastai: A Layered API for Deep Learning. http://dx.doi.org/10.3390/info11020108

For Jupyter notebook and code: https://medium.com/@pieter.jooste.jp/machine-learning-fastai-triage-ill-baby-6fa28909feee

