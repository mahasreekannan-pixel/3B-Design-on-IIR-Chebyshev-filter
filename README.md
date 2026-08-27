# IIR-FILTER-DESIGN

# EXP 3 B: DESIGN OF LOW PASS CHEBYSHEV IIR FILTER USING BILINEAR TRANSFORMATION

# AIM: 

# To a design of low pass Chebyshev IIR filter using Bilinear Transformation.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
<br>clc ; 
<br>close ; 
<br>wp=input('Enter the pass band frequency (Radians )= ' ); 
<br>ws=input('Enter the stop band frequency (Radians )= ' ); 
<br>alphap=input( ' Enter the pass band attenuation (dB)=' ); 
<br>alphas=input( ' Enter the stop band attenuation(dB)=' ); 
<br>T=input('Enter the Value of sampling Time='); 
<br>//Pre warping- Bilinear Transformation 
<br>omegap=(2/T)*tan(wp/2); 
<br>disp(omegap,'omegap='); 
<br>omegas=(2/T)*tan(ws/2); 
<br>disp(omegas,'omegas='); 
<br>//Order of the filter 
<br>N=acosh(sqrt(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1)))/(acosh(omegas/omegap)); 
<br>disp(N,'N='); 
<br>N=ceil(N); 
<br>disp(N,'Round off value of N='); 
<br>//Cut off frequency 
<br>omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N))); 
<br>disp(omegac,'omegac='); 
<br>Epsilon = sqrt ((10^(0.1*alphap))-1); 
<br>disp(Epsilon,'Epsilon='); 
<br>[pols ,gn] = zpch1(N, Epsilon,omegap ); 
<br>disp(gn,'Gain'); 
<br>disp(pols,'Poles'); 
<br>hs=poly(gn,'s','coeff')/real(poly(pols,'s')); 
<br>disp(hs,'Analog Low pass Chebyshev Filter Transfer function'); 
<br>z=poly(0,'z');//Defining variable z 
<br>Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation 
<br>disp(Hz,'Digital LPF Transfer function H(Z)='); 
<br>HW=frmag(Hz,512); // Frequency response 
<br>w=0:%pi/511:%pi ; 
<br>plot(w/%pi,abs(HW)); 
<br>xlabel(' Normalized Digital Frequency w'); 
<br>ylabel('Magnitude '); 
<br>title(' Frequency Response of Chebyshev IIR LPF'); 


# OUTPUT: 


# RESULT: 
Thus design of Chebyshev Low pass IIR filter waveforms were plotted and output was
verified.
