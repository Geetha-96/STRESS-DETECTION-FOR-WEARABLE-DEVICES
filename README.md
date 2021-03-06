{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "name": "KNeighbours Classifer.ipynb",
      "provenance": [],
      "collapsed_sections": []
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "accelerator": "GPU"
  },
  "cells": [
    {
      "cell_type": "code",
      "metadata": {
        "id": "xrHoFTwCQtGB",
        "colab_type": "code",
        "colab": {}
      },
      "source": [
        "import numpy as np\n",
        "\n",
        "import pandas as pd\n",
        "from sklearn import datasets, svm, metrics\n",
        "import matplotlib.pyplot as plt"
      ],
      "execution_count": 0,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "gOQVdHCz0ZQ0",
        "colab_type": "code",
        "colab": {}
      },
      "source": [
        "from google.colab import drive\n",
        "drive.mount('/content/drive')"
      ],
      "execution_count": 0,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "TmHsAC4jSYI9",
        "colab_type": "code",
        "colab": {}
      },
      "source": [
        "trainFile = pd.read_csv('/content/drive/My Drive/TechJam/train.csv').drop(columns=\"datasetId\")\n",
        "testFile = pd.read_csv('/content/drive/My Drive/TechJam/test.csv').drop(columns=\"datasetId\")"
      ],
      "execution_count": 0,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "t3xkR7WAWfVO",
        "colab_type": "code",
        "colab": {}
      },
      "source": [
        "#features\n",
        "X_train = trainFile.drop(columns='condition')\n",
        "y_train = trainFile['condition']\n",
        "X_test = testFile.drop(columns='condition')\n",
        "y_test = testFile['condition']"
      ],
      "execution_count": 0,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "INrVmaTjYX1j",
        "colab_type": "code",
        "outputId": "0cf265a2-ffc9-459b-b809-041ca5e208ed",
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 51
        }
      },
      "source": [
        "from sklearn.neighbors import KNeighborsClassifier\n",
        "knn = KNeighborsClassifier()\n",
        "knn.fit(X_train, y_train)\n",
        "print('Accuracy of K-NN classifier on training set: {:.2f}'\n",
        "     .format(knn.score(X_train, y_train)))\n",
        "print('Accuracy of K-NN classifier on test set: {:.2f}'\n",
        "     .format(knn.score(X_test, y_test)))"
      ],
      "execution_count": 7,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "Accuracy of K-NN classifier on training set: 1.00\n",
            "Accuracy of K-NN classifier on test set: 0.99\n"
          ],
          "name": "stdout"
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "_EImbKQpKx23",
        "colab_type": "code",
        "outputId": "84a158f1-3092-4b98-9bfa-2da1443653ab",
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 34
        }
      },
      "source": [
        "i=1\n",
        "knn.predict([X_test.iloc[i]])"
      ],
      "execution_count": 10,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "array(['time pressure'], dtype=object)"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 10
        }
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "yQxLkl7iBEzK",
        "colab_type": "code",
        "outputId": "e8d6fb66-ef30-4bb5-db66-d2e897bd03bc",
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 605
        }
      },
      "source": [
        "print(X_test.iloc[i])"
      ],
      "execution_count": 0,
      "outputs": [
        {
          "output_type": "stream",
          "text": [
            "MEAN_RR               831.632295\n",
            "MEDIAN_RR             836.596795\n",
            "SDRR                   62.069042\n",
            "RMSSD                  12.576667\n",
            "SDSD                   12.576557\n",
            "SDRR_RMSSD              4.935254\n",
            "HR                     72.562697\n",
            "pNN25                   4.533333\n",
            "pNN50                   0.266667\n",
            "SD1                     8.895937\n",
            "SD2                    87.326938\n",
            "KURT                   -0.087277\n",
            "SKEW                   -0.226072\n",
            "MEAN_REL_RR             0.000055\n",
            "MEDIAN_REL_RR           0.000707\n",
            "SDRR_REL_RR             0.015505\n",
            "RMSSD_REL_RR            0.008243\n",
            "SDSD_REL_RR             0.008243\n",
            "SDRR_RMSSD_REL_RR       1.881017\n",
            "KURT_REL_RR            -0.087277\n",
            "SKEW_REL_RR            -0.226072\n",
            "VLF                  1534.857041\n",
            "VLF_PCT                71.422649\n",
            "LF                    586.603990\n",
            "LF_PCT                 27.296882\n",
            "LF_NU                  95.519285\n",
            "HF                     27.517012\n",
            "HF_PCT                  1.280470\n",
            "HF_NU                   4.480715\n",
            "TP                   2148.978043\n",
            "LF_HF                  21.317867\n",
            "HF_LF                   0.046909\n",
            "sampen                  2.177956\n",
            "higuci                  1.202543\n",
            "Name: 5, dtype: float64\n"
          ],
          "name": "stdout"
        }
      ]
    }
  ]
}
