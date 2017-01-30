# *Teddy*

## The catalogue

This galaxy catalogue has been created isolate the effect of incomplete spectroscopic sample coverage in the determination of photometric redshifts.

The catalogue has four subsamples: Teddy A,B,C and D.

* **Teddy A**: was randomly drawn from the [SDSS DR12](http://www.sdss.org/dr12/) spectroscopic sample, observing the selection criteria described in [Beck et al, 2016]() - section2.1. This should be used as a training/calibration set.

* **Teddy B**: the same as Teddy A, but this should act as the spectroscopic validation set.

* **Teddy C**: has the same coverage in magnitude/color space as Teddy A/B but follows a different underlying distribution.  This should be another validation set.

* **Teddy D**: has a larger coverage in magnitude/color space when compared to Teddy A/B. This is the third validation set.

All objects in this catalog were taken from the SDSS DR12 spectroscopic sample. All magnitudes are SDSS dereddened modelMag magnitudes (dered_[ugriz]).
	
## The machine learning catalogue files

* teddy_[ABCD]
	
	Columns: id mag_r u-g g-r r-i i-z z_spec feat1 feat2 feat3 feat4 feat5

	*id*: SDSS ObjID  
	*mag_r*: dered_r magnitude  
	*u-g* to *i-z*: respective dereddened colours  
	*z_spec*: spectroscopic redshift  
	*feat1*: mag_r normalized to have 0 mean and 1 stdev (mean and stdev were computed for the Teddy A set)
	*feat2*: u-g colour normalized similarly  
	*feat3*: g-r colour normalized similarly  
	*feat4*: r-i colour normalized similarly  
	*feat5*: i-z colour normalized similarly  
	
	
## The template fitting catalogue files

* forTemplateBased/teddyT_[ABCD]
	
	The galaxies are in the same order as teddy_[ABCD].  
	
	Columns: id u g r i z uErr gErr rErr iErr zErr redshift redshiftErr  

	*id*: SDSS ObjID  
	*[ugriz]*: dered_[ugriz] magnitude  
	*[ugriz]Err*: modelMagErr_[ugriz] magnitude error  
	*redshift*: spectroscopic redshift  
	*redshiftErr*: error of the spectroscopic redshift  

	forTemplateBased/teddyT_A_clean has the same structure, but also requires the clean=1 SDSS photometry flag (not used in the paper).  

## The weight files

* weights_for_[BCD]
	
	Single column, a density ratio approach was used to calculate a weight for each galaxy in the happy_A training sample, in order. The procedure is described in [Kremer et al, 2015](http://adsabs.harvard.edu/abs/2015A%26C....12...67K). The corresponding code can be found in [this repository](https://github.com/kremerj/nnratio).  
	
	The [BCD] tag corresponds to the set of weights that should be used when approximating the [BCD] validation sets, respectively.  

