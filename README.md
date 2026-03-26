# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc ; 
close ; 
wp=input('Enter the pass band frequency (Radians )= ' ); 
ws=input('Enter the stop band frequency (Radians )= ' ); 
alphap=input( ' Enter the pass band attenuation (dB)=' ); 
alphas=input( ' Enter the stop band attenuation(dB)=' ); 
T=input('Enter the Value of sampling Time=');

//Pre warping- Bilinear Transformation 
omegap=(2/T)*tan(wp/2); 
disp(omegap,'omegap='); 
omegas=(2/T)*tan(ws/2); 
disp(omegas,'omegas=');

//Order of the filter 
N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap)); 
disp(N,'N='); 
N=ceil(N); 
disp(N,'Round off value of N=');

//Cut off frequency 
omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N))); 
disp(omegac,'omegac='); 
 
disp('Normalised Analog LPF Transfer function H(S)='); 
hs_Normalised = analpf(N,'butt',[0,0],1); 
disp(hs_Normalised); 
 
disp('Analog LPF Transfer function H(S)='); 
hs= analpf(N,'butt',[0,0],omegac); 
disp(hs); 
z=poly(0,'z');//Defining variable z 
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation 
disp('Digital LPF Transfer function H(Z)='); 
disp(Hz);
HW=frmag(Hz,512); // Frequency response 
w=0:%pi/511:%pi ; 
plot(w/%pi,abs(HW)); 
xlabel(' Normalized Digital Frequency w'); 
ylabel('Magnitude ');
title(' Frequency Response of Butterworth IIR LPF');

```

# CALCULATION :
<img width="973" height="1550" alt="image" src="https://github.com/user-attachments/assets/592e25d3-e787-40fa-9af2-527f9c2c84bf" />
<img width="921" height="1532" alt="image" src="https://github.com/user-attachments/assets/8f70f8e8-8bca-4b10-a538-c1d0a1970984" />
<img width="1600" height="762" alt="image" src="https://github.com/user-attachments/assets/bf8bd030-d0cf-4451-b40e-dbb9fad3b72c" />


# OUTPUT: 
<img width="756" height="721" alt="image" src="https://github.com/user-attachments/assets/1bc7ae7f-0846-4ee7-87ee-751edd763c27" />


# RESULT: 
Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified

