# *Happy*

## The catalogue

This galaxy catalogue has been created to test how photo-z estimation is affected by a differing photometric error (and feature) distribution between photometric and spectroscopic samples, resembling the case of [SDSS-DR12](http://www.sdss.org/dr12/).

The catalogue has four subsamples: Happy A,B,C and D.

* **Happy A**: resembles the SDSS DR12 spectroscopic sample in the distribution of all observables. This should be used as a training/calibration set.

* **Happy B**: the same as Happy A, but this should act as the spectroscopic validation set.

* **Happy C**: has the same range of photometric errors as Happy A/B, and essentially the same colour/magnitude coverage, but the distribution of errors is much more weighted towards high errors. Also, the feature distribution closely resembles the SDSS DR12 photometric sample within the coverage. This should be another validation set.

* **Happy D**: resembles the SDSS-DR12 photometric sample in the distribution of all observables. This is the third validation set.

All magnitudes are SDSS dereddened modelMag magnitudes (dered_[ugriz]).
	
## The machine learning catalogue files

* happy_[ABCD]
	
	Columns: id mag_r u-g g-r r-i i-z z_spec feat1 feat2 feat3 feat4 feat5

	id: SDSS ObjID  
	mag_r: dered_r magnitude  
	u-g to i-z: respective dereddened colours  
	z_spec: spectroscopic redshift  
	feat1: mag_r scaled to have 0 mean and 1 stdev (scaling done in the SDSS DR12 spectro sample)  
	feat2: u-g colour scaled similarly  
	feat3: g-r colour scaled similarly  
	feat4: r-i colour scaled similarly  
	feat5: i-z colour scaled similarly  
	
	
## The template fitting catalogue files

* forTemplateBased/happyT_[ABCD]
	
	The galaxies are in the same order as happy_[ABCD].  
	
	Columns: id u g r i z uErr gErr rErr iErr zErr redshift redshiftErr  

	id: SDSS ObjID  
	[ugriz]: dered_[ugriz] magnitude  
	[ugriz]Err: modelMagErr_[ugriz] magnitude error  
	redshift: spectroscopic redshift  
	redshiftErr: error of the spectroscopic redshift  

	forTemplateBased/happyT_A_clean has the same structure, but also requires the clean=1 SDSS photometry flag (not used in the paper).  

## The weight files

* weights_for_[BCD]
	
	Single column, a nearest neighbour-approximated weight for each galaxy in the happy_A training sample, in order.  
	
	The [BCD] tag corresponds to the set of weights that should be used when approximating the [BCD] validation sets, respectively.  
