<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]


<h3 align="center">Survival prediction in lung cancer patients based on chest CT scans</h3>

  <p align="center">
    Using 3D Conv nets, nonlinear cox-proportional hazards, and concordance index
    <br />
    <a href="https://github.com/masadeghi/lung_cancer_ctscan_survival"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/masadeghi/lung_cancer_ctscan_survival/issues">Report Bug</a>
    ·
    <a href="https://github.com/masadeghi/lung_cancer_ctscan_survival/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

In this project, I've used chest CT scans of lung cancer patients from the [NSCLC-Radiomics dataset from The Cancer Imaging Archive (TCIA)](https://wiki.cancerimagingarchive.net/display/Public/NSCLC-Radiomics)
to predict their survival. This dataset was originally used for [this study published in Nature Communications](https://www.nature.com/ncomms/2014/140603/ncomms5006/full/ncomms5006.html) and contains
DICOM files of chest CT scans, survival data, and event status (death) data to identify right censored data points.

To estimate the survival model for these patients, I apply a 3D convolutional neural network on their CT scans to output a risk score for each patient. The model is trained through
evaluating this risk score using Harrell's concordance index in the validation set and cox-proportional hazards model for each batch in the training set. The CNN model
architecture has been adapted from [here](https://keras.io/examples/vision/3D_image_classification/) and the architecture for prediciting survival models using neural
networks has been adapted from [here](https://k-d-w.org/blog/2020/05/survival-analysis-for-deep-learning-tutorial-for-tensorflow-2/).

References:

Aerts, H. J. W. L., Wee, L., Rios Velazquez, E., Leijenaar, R. T. H., Parmar, C., Grossmann, P., Carvalho, S., Bussink, J., Monshouwer, R., Haibe-Kains, B., Rietveld, D., Hoebers, F., Rietbergen, M. M., Leemans, C. R., Dekker, A., Quackenbush, J., Gillies, R. J., Lambin, P. (2019). Data From NSCLC-Radiomics [Data set]. The Cancer Imaging Archive. https://doi.org/10.7937/K9/TCIA.2015.PF0M9REI 

Aerts, H. J. W. L., Velazquez, E. R., Leijenaar, R. T. H., Parmar, C., Grossmann, P., Carvalho, S., Bussink, J., Monshouwer, R., Haibe-Kains, B., Rietveld, D., Hoebers, F., Rietbergen, M. M., Leemans, C. R., Dekker, A., Quackenbush, J., Gillies, R. J., Lambin, P. (2014, June 3). Decoding tumour phenotype by noninvasive imaging using a quantitative radiomics approach. Nature Communications. Nature Publishing Group. https://doi.org/10.1038/ncomms5006

Clark K, Vendt B, Smith K, Freymann J, Kirby J, Koppel P, Moore S, Phillips S, Maffitt D, Pringle M, Tarbox L, Prior F. The Cancer Imaging Archive (TCIA): Maintaining and Operating a Public Information Repository, Journal of Digital Imaging, Volume 26, Number 6, December, 2013, pp 1045-1057. https://doi.org/10.1007/s10278-013-9622-7

<p align="right">(<a href="#readme-top">back to top</a>)</p>



### Built With

* Python v3.7.15
* TensorFlow v2.9.2

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started

The data used in this study consists of two parts. The imaging data (25GB) is imported directly from the TCIA as described [here](https://github.com/kirbyju/TCIA_Notebooks/blob/main/TCIA_REST_API_Downloads.ipynb).
The survival and event status data can be downloaded using [this link](https://wiki.cancerimagingarchive.net/download/attachments/16056854/NSCLC%20Radiomics%20Lung1.clinical-version3-Oct%202019.csv?version=1&modificationDate=1572013183040&api=v2).
I have renamed the file containing survival information as "NSCLC-Radiomics clincal data.csv" for use in the script. If you run the code in Colab, you'll have to manually upload the renamed file to Colab's
temporary storage folder.

### Installation

The required dependencies are all installed at the beginning of the notebook. Note that if you run this code in Colab, its intrinsic scikit-learn module is not
compatible with the scikit-survival module that is used for survival analysis. As a result, scikit-learn is uninstalled and reinstalled at the beginning of the
notebook, and the runtime must be restarted afterwards for the scikit-learn update to take effect.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage

This project is an example of analyzing biomedical data using deep learning to predict survival and hazard functions.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Amin Sadeghi - masadeghi6@gmail.com

Project Link: [https://github.com/masadeghi/lung_cancer_ctscan_survival](https://github.com/masadeghi/lung_cancer_ctscan_survival)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/masadeghi/lung_cancer_ctscan_survival.svg?style=for-the-badge
[contributors-url]: https://github.com/masadeghi/lung_cancer_ctscan_survival/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/masadeghi/lung_cancer_ctscan_survival.svg?style=for-the-badge
[forks-url]: https://github.com/masadeghi/lung_cancer_ctscan_survival/network/members
[stars-shield]: https://img.shields.io/github/stars/masadeghi/lung_cancer_ctscan_survival.svg?style=for-the-badge
[stars-url]: https://github.com/masadeghi/lung_cancer_ctscan_survival/stargazers
[issues-shield]: https://img.shields.io/github/issues/masadeghi/lung_cancer_ctscan_survival.svg?style=for-the-badge
[issues-url]: https://github.com/masadeghi/lung_cancer_ctscan_survival/issues
[license-shield]: https://img.shields.io/github/license/masadeghi/lung_cancer_ctscan_survival.svg?style=for-the-badge
[license-url]: https://github.com/masadeghi/lung_cancer_ctscan_survival/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/mohammad-amin-sadeghi-md/
