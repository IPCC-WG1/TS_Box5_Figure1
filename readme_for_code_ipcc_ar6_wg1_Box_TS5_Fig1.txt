##########################################################################
# ---------------------------------------------------------------------------------------------------------------------
# This is Python code to produce IPCC AR6 WGI Figure Box TS.5, Figure 1
# Creator: Christopher D. Jones, Met Office Hadley Centre; Charles Koven,Lawrence Berkeley National Laboratory, USA; 
           Zebedee Nicholls, University of Melbourne, Australia; Spencer Liddicoat, Met Office Hadley Centre; 
           Malte Meinshausen, University of Melbourne; Jared Lewis,University of Melbourne;
# Contact: chris.d.jones@metoffice.gov.uk, cdkoven@lbl.gov, zebedee.nicholls@climate-energy-college.org, 
spencer.liddicoat@metoffice.gov.uk, malte.meinshausen@unimelb.edu.au, jared.lewis@climate-resource.com
# Last updated on: May 25th, 2022
# --------------------------------------------------------------------------------------------------------------------
#
# - Code functionality: The python script TS_C_cycle.py will read data and recreate the entire multi-panel figure from the following data files:
# - Input data: carbon cycle feedback sensitivities from the CMIP6 models (courtesy Charlie Koven):

- carbon_feedback_parameters.nc

---
CO2 concentration data used as input to the concentration driven historical and ssp simulations:
CMIP6_HIST_CO2.dat
CMIP6_SSP2300_CO2.dat
CMIP6_SSP_CO2.dat

CO2 concentrations from CMIP6 models from the emissions-driven SSP5-8.5 simulation:
CMIP6_e-CO2.dat

---

CO2 concentrations from MAGICC 7.5.1 model for the other scenarios (courtesy Zeb Nicholls and MAGICC team):

MAGICCv7.5.1_atmospheric-co2_esm-ssp119.nc
MAGICCv7.5.1_atmospheric-co2_esm-ssp126.nc
MAGICCv7.5.1_atmospheric-co2_esm-ssp245.nc
MAGICCv7.5.1_atmospheric-co2_esm-ssp370.nc
MAGICCv7.5.1_atmospheric-co2_esm-ssp534-over.nc
MAGICCv7.5.1_atmospheric-co2_esm-ssp585.nc

MAGICC is maintained and developed by Malte Meinshausen (<malte.meinshausen@unimelb.edu.au>),
Jared Lewis (<jared.lewis@climate-resource.com>) and Zebedee Nicholls (<zebedee.nicholls@climate-energy-college.org>).
If you have any questions about MAGICC's output or would like to use it in a publication, please contact
Malte Meinshausen (<malte.meinshausen@unimelb.edu.au>),
Jared Lewis (<jared.lewis@climate-resource.com>) and Zebedee Nicholls (<zebedee.nicholls@climate-energy-college.org>).
The setup used to generate this data is described extensively in Cross-chapter Box 7.1 and is based on
Meinshausen et al. [2009](https://doi.org/10.1038/nature08017), [2011](https://doi.org/10.5194/acp-11-1417-2011) and [2020](https://doi.org/10.5194/gmd-13-3571-2020).

---

Carbon fluxes and derived emissions from the CMIP6 models up to 2100 (courtesy Spencer Liddicoat):
ffEmsHistoricalSsp119_GtCyr.txt
ffEmsHistoricalSsp126_GtCyr.txt
ffEmsHistoricalSsp245_GtCyr.txt
ffEmsHistoricalSsp370_GtCyr.txt
ffEmsHistoricalSsp434_GtCyr.txt
ffEmsHistoricalSsp460_GtCyr.txt
ffEmsHistoricalSsp534os_GtCyr.txt
ffEmsHistoricalSsp585_GtCyr.txt
global_total_FGCO2_GtC_yr_HistoricalSsp119.txt
global_total_FGCO2_GtC_yr_HistoricalSsp126.txt
global_total_FGCO2_GtC_yr_HistoricalSsp245.txt
global_total_FGCO2_GtC_yr_HistoricalSsp370.txt
global_total_FGCO2_GtC_yr_HistoricalSsp434.txt
global_total_FGCO2_GtC_yr_HistoricalSsp460.txt
global_total_FGCO2_GtC_yr_HistoricalSsp534os.txt
global_total_FGCO2_GtC_yr_HistoricalSsp585.txt
global_total_NBP_GtC_yr_HistoricalSsp119.txt
global_total_NBP_GtC_yr_HistoricalSsp126.txt
global_total_NBP_GtC_yr_HistoricalSsp245.txt
global_total_NBP_GtC_yr_HistoricalSsp370.txt
global_total_NBP_GtC_yr_HistoricalSsp434.txt
global_total_NBP_GtC_yr_HistoricalSsp460.txt
global_total_NBP_GtC_yr_HistoricalSsp534os.txt
global_total_NBP_GtC_yr_HistoricalSsp585.txt

# multi-model, multi-scenario flux data from Liddicoat et al., 2020
# https://journals.ametsoc.org/view/journals/clim/aop/JCLI-D-19-0991.1/JCLI-D-19-0991.1.xml

---

Carbon fluxes from the CMIP6 models up to 2300:
CESM2-WACCM_fgco2.dat
CESM2-WACCM_nbp.dat
CanESM5_fgco2.dat
CanESM5_nbp.dat
IPSL-CM6A-LR_fgco2.dat
IPSL-CM6A-LR_nbp.dat
UKESM1-0-LL_fgco2.dat
UKESM1-0-LL_nbp.dat 
               
# - Output variables: 
#
# ----------------------------------------------------------------------------------------------------
# Information on  the software used
# - Software Version: Python 3.6.6, Iris 3.0.1
# - Landing page to access the software:  
# - Operating System: 
# - Environment required to compile and run: 
#  ----------------------------------------------------------------------------------------------------
#
#  License: Apache 2.0
# ----------------------------------------------------------------------------------------------------
# How to cite:
# When citing this code, please include both the code citation and the following citation for the related report component:
Arias, P.A., N. Bellouin, E. Coppola, R.G. Jones, G. Krinner, J. Marotzke, V. Naik, M.D. Palmer, G.-K. Plattner, J. Rogelj, M. Rojas, J. Sillmann, T. Storelvmo, P.W. Thorne, B. Trewin, K. Achuta Rao, B. Adhikary, R.P. Allan, K. Armour, G. Bala, R. Barimalala, S. Berger, J.G. Canadell, C. Cassou, A. Cherchi, W. Collins, W.D. Collins, S.L. Connors, S. Corti, F. Cruz, F.J. Dentener, C. Dereczynski, A. Di Luca, A. Diongue Niang, F.J. Doblas-Reyes, A. Dosio, H. Douville, F. Engelbrecht, V. Eyring, E. Fischer, P. Forster, B. Fox-Kemper, J.S. Fuglestvedt, J.C. Fyfe, N.P. Gillett, L. Goldfarb, I. Gorodetskaya, J.M. Gutierrez, R. Hamdi, E. Hawkins, H.T. Hewitt, P. Hope, A.S. Islam, C. Jones, D.S. Kaufman, R.E. Kopp, Y. Kosaka, J. Kossin, S. Krakovska, J.-Y. Lee, J. Li, T. Mauritsen, T.K. Maycock, M. Meinshausen, S.-K. Min, P.M.S. Monteiro, T. Ngo-Duc, F. Otto, I. Pinto, A. Pirani, K. Raghavan, R. Ranasinghe, A.C. Ruane, L. Ruiz, J.-B. Sallée, B.H. Samset, S. Sathyendranath, S.I. Seneviratne, A.A. Sörensson, S. Szopa, I. Takayabu, A.-M. Tréguier, B. van den Hurk, R. Vautard, K. von Schuckmann, S. Zaehle, X. Zhang, and K. Zickfeld, 2021: Technical Summary. In Climate Change 2021: The Physical Science Basis. Contribution of Working Group I to the Sixth Assessment Report of the Intergovernmental Panel on Climate Change [Masson-Delmotte, V., P. Zhai, A. Pirani, S.L. Connors, C. Péan, S. Berger, N. Caud, Y. Chen, L. Goldfarb, M.I. Gomis, M. Huang, K. Leitzell, E. Lonnoy, J.B.R. Matthews, T.K. Maycock, T. Waterfield, O. Yelekçi, R. Yu, and B. Zhou (eds.)]. Cambridge University Press, Cambridge, United Kingdom and New York, NY, USA, pp. 33−144. doi: 10.1017/9781009157896.002.
########################################################################