For the Doppler simulation:
[] change geometry to try and remove the symmetry problem/ figure out with which cases the symmetry problem vanishes. It is a sort of observability analysis
	same plane but different radius
	relative inclination
	RAAN/phase geometry
	initial separation
	observation arc
	one orbit more eccentric
[] alongside the above, try different scenarios which will later be used as a basis to compare the AI with
	include short observation window 

Future: Go back through the chain before going forward
[] Look into how the signals are detected and how the Doppler shift is calculated
[] Fourier transformation on the received signal (VHF vs S-band, VHF doesn't get much Doppler shift but shorter observation window?)
[] Calculate errors carried along the measurement
(signal detection -> Doppler calculation -> velocity calculation -> relative position -> PINNs)

PINNs
[] different AIs? - spikes, NN

Presentation with Luis: 
[]what is the project 
[] key milestones 
[] Ghant chart (in detail for the next 6 months and rough year + conferences or papers) 

Conference paper:
	ISE
	Citech - get some of the Doppler stuff working by the end of October
	Astrodynamics specialist
	Space fly mechanics 

- Avoid doing tests or adding complexity through things as noise, it has to be more mathematics focused, not engineering problems.
- Focus on relative orbit, not the actual orbit of the satellite
- Ensure that my Doppler calculation is directly related to the velocity change
- Also possibly look into angles only OD or range only OD for the AI? 
- Journal paper (after conference paper) before second year review (before the viva would be great)
- How doppler/ angle works from an event base. 
