
# Hi, I'm Moksh Verma! 👋


# ML Project : "Loan Approval Prediction Model"

### ~ Financial Loan approval Prediction Machine Learning Model by using Python and ML Modules.


# What is the Purpose of this Project?

This Random Forest Classification Machine Learning Model helps in Predicting whether the Candidate is capable of Repaying the Loan. Based on some Labels/Attributes this Machine Learning Model Predicts whether to Grant Loan to that Candidate or not!

# Industry Requirement?

This type of Random Forest Classification Models are highly used in **Finance Industry**(Corporate Banks and more).

## Screenshots

![Home Page](https://github.com/mokshverma-dev/Elemon/blob/main/home_page.png)
![Components Page](https://github.com/mokshverma-dev/Elemon/blob/main/components_page.png)
![Component Page View](https://github.com/mokshverma-dev/Elemon/blob/main/component_page_view.png)

# Dataset for Training Model

[loan_grant_training_data.csv](https://github.com/mokshverma-dev/loan-approval-prediction-model/blob/main/loan_grant_training_data.csv)

## Tech Stack

**Client:**   TailwindCSS

**Server:**   Django

**Database:**   SQLite


## Related

Here are some related projects

[Resoorces.com](https://github.com/mokshverma-dev/Resoorces)


## Authors

- [@mokshverma_](https://www.instagram.com/mokshverma_/)




{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 27,
   "id": "0b501984",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Loan_ID</th>\n",
       "      <th>Gender</th>\n",
       "      <th>Married</th>\n",
       "      <th>Dependents</th>\n",
       "      <th>Education</th>\n",
       "      <th>Self_Employed</th>\n",
       "      <th>ApplicantIncome</th>\n",
       "      <th>CoapplicantIncome</th>\n",
       "      <th>LoanAmount</th>\n",
       "      <th>Loan_Amount_Term</th>\n",
       "      <th>Credit_History</th>\n",
       "      <th>Property_Area</th>\n",
       "      <th>Loan_Status</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>LP001002</td>\n",
       "      <td>Male</td>\n",
       "      <td>No</td>\n",
       "      <td>0</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>5849</td>\n",
       "      <td>0.0</td>\n",
       "      <td>120.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Urban</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>LP001003</td>\n",
       "      <td>Male</td>\n",
       "      <td>Yes</td>\n",
       "      <td>1</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>4583</td>\n",
       "      <td>1508.0</td>\n",
       "      <td>128.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Rural</td>\n",
       "      <td>N</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>LP001005</td>\n",
       "      <td>Male</td>\n",
       "      <td>Yes</td>\n",
       "      <td>0</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>Yes</td>\n",
       "      <td>3000</td>\n",
       "      <td>0.0</td>\n",
       "      <td>66.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Urban</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>LP001006</td>\n",
       "      <td>Male</td>\n",
       "      <td>Yes</td>\n",
       "      <td>0</td>\n",
       "      <td>Not Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>2583</td>\n",
       "      <td>2358.0</td>\n",
       "      <td>120.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Urban</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>LP001008</td>\n",
       "      <td>Male</td>\n",
       "      <td>No</td>\n",
       "      <td>0</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>6000</td>\n",
       "      <td>0.0</td>\n",
       "      <td>141.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Urban</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "    Loan_ID Gender Married Dependents     Education Self_Employed  \\\n",
       "0  LP001002   Male      No          0      Graduate            No   \n",
       "1  LP001003   Male     Yes          1      Graduate            No   \n",
       "2  LP001005   Male     Yes          0      Graduate           Yes   \n",
       "3  LP001006   Male     Yes          0  Not Graduate            No   \n",
       "4  LP001008   Male      No          0      Graduate            No   \n",
       "\n",
       "   ApplicantIncome  CoapplicantIncome  LoanAmount  Loan_Amount_Term  \\\n",
       "0             5849                0.0       120.0             360.0   \n",
       "1             4583             1508.0       128.0             360.0   \n",
       "2             3000                0.0        66.0             360.0   \n",
       "3             2583             2358.0       120.0             360.0   \n",
       "4             6000                0.0       141.0             360.0   \n",
       "\n",
       "   Credit_History Property_Area Loan_Status  \n",
       "0             1.0         Urban           Y  \n",
       "1             1.0         Rural           N  \n",
       "2             1.0         Urban           Y  \n",
       "3             1.0         Urban           Y  \n",
       "4             1.0         Urban           Y  "
      ]
     },
     "execution_count": 27,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "import pandas as pd\n",
    "data=pd.read_csv('loan_grant_training_data.csv')\n",
    "data.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "id": "21529514",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Loan_ID</th>\n",
       "      <th>Gender</th>\n",
       "      <th>Married</th>\n",
       "      <th>Dependents</th>\n",
       "      <th>Education</th>\n",
       "      <th>Self_Employed</th>\n",
       "      <th>ApplicantIncome</th>\n",
       "      <th>CoapplicantIncome</th>\n",
       "      <th>LoanAmount</th>\n",
       "      <th>Loan_Amount_Term</th>\n",
       "      <th>Credit_History</th>\n",
       "      <th>Property_Area</th>\n",
       "      <th>Loan_Status</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>609</th>\n",
       "      <td>LP002978</td>\n",
       "      <td>Female</td>\n",
       "      <td>No</td>\n",
       "      <td>0</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>2900</td>\n",
       "      <td>0.0</td>\n",
       "      <td>71.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Rural</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>610</th>\n",
       "      <td>LP002979</td>\n",
       "      <td>Male</td>\n",
       "      <td>Yes</td>\n",
       "      <td>3+</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>4106</td>\n",
       "      <td>0.0</td>\n",
       "      <td>40.0</td>\n",
       "      <td>180.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Rural</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>611</th>\n",
       "      <td>LP002983</td>\n",
       "      <td>Male</td>\n",
       "      <td>Yes</td>\n",
       "      <td>1</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>8072</td>\n",
       "      <td>240.0</td>\n",
       "      <td>253.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Urban</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>612</th>\n",
       "      <td>LP002984</td>\n",
       "      <td>Male</td>\n",
       "      <td>Yes</td>\n",
       "      <td>2</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>7583</td>\n",
       "      <td>0.0</td>\n",
       "      <td>187.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Urban</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>613</th>\n",
       "      <td>LP002990</td>\n",
       "      <td>Female</td>\n",
       "      <td>No</td>\n",
       "      <td>0</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>Yes</td>\n",
       "      <td>4583</td>\n",
       "      <td>0.0</td>\n",
       "      <td>133.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>0.0</td>\n",
       "      <td>Semiurban</td>\n",
       "      <td>N</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "      Loan_ID  Gender Married Dependents Education Self_Employed  \\\n",
       "609  LP002978  Female      No          0  Graduate            No   \n",
       "610  LP002979    Male     Yes         3+  Graduate            No   \n",
       "611  LP002983    Male     Yes          1  Graduate            No   \n",
       "612  LP002984    Male     Yes          2  Graduate            No   \n",
       "613  LP002990  Female      No          0  Graduate           Yes   \n",
       "\n",
       "     ApplicantIncome  CoapplicantIncome  LoanAmount  Loan_Amount_Term  \\\n",
       "609             2900                0.0        71.0             360.0   \n",
       "610             4106                0.0        40.0             180.0   \n",
       "611             8072              240.0       253.0             360.0   \n",
       "612             7583                0.0       187.0             360.0   \n",
       "613             4583                0.0       133.0             360.0   \n",
       "\n",
       "     Credit_History Property_Area Loan_Status  \n",
       "609             1.0         Rural           Y  \n",
       "610             1.0         Rural           Y  \n",
       "611             1.0         Urban           Y  \n",
       "612             1.0         Urban           Y  \n",
       "613             0.0     Semiurban           N  "
      ]
     },
     "execution_count": 28,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data.tail()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 29,
   "id": "1c5e47f7",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(614, 13)"
      ]
     },
     "execution_count": 29,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data.shape"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 30,
   "id": "654efbeb",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Number of Rows 614\n",
      "Number of Columns 13\n"
     ]
    }
   ],
   "source": [
    "print(\"Number of Rows\", data.shape[0])\n",
    "print(\"Number of Columns\", data.shape[1])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 31,
   "id": "a82e5d2c",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 614 entries, 0 to 613\n",
      "Data columns (total 13 columns):\n",
      " #   Column             Non-Null Count  Dtype  \n",
      "---  ------             --------------  -----  \n",
      " 0   Loan_ID            614 non-null    object \n",
      " 1   Gender             614 non-null    object \n",
      " 2   Married            614 non-null    object \n",
      " 3   Dependents         611 non-null    object \n",
      " 4   Education          614 non-null    object \n",
      " 5   Self_Employed      608 non-null    object \n",
      " 6   ApplicantIncome    614 non-null    int64  \n",
      " 7   CoapplicantIncome  614 non-null    float64\n",
      " 8   LoanAmount         593 non-null    float64\n",
      " 9   Loan_Amount_Term   601 non-null    float64\n",
      " 10  Credit_History     564 non-null    float64\n",
      " 11  Property_Area      614 non-null    object \n",
      " 12  Loan_Status        614 non-null    object \n",
      "dtypes: float64(4), int64(1), object(8)\n",
      "memory usage: 62.5+ KB\n"
     ]
    }
   ],
   "source": [
    "data.info()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 32,
   "id": "dad9a77d",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Loan_ID               0\n",
       "Gender                0\n",
       "Married               0\n",
       "Dependents            3\n",
       "Education             0\n",
       "Self_Employed         6\n",
       "ApplicantIncome       0\n",
       "CoapplicantIncome     0\n",
       "LoanAmount           21\n",
       "Loan_Amount_Term     13\n",
       "Credit_History       50\n",
       "Property_Area         0\n",
       "Loan_Status           0\n",
       "dtype: int64"
      ]
     },
     "execution_count": 32,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data.isnull().sum()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 33,
   "id": "453143e2",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Loan_ID              0.000000\n",
       "Gender               0.000000\n",
       "Married              0.000000\n",
       "Dependents           0.488599\n",
       "Education            0.000000\n",
       "Self_Employed        0.977199\n",
       "ApplicantIncome      0.000000\n",
       "CoapplicantIncome    0.000000\n",
       "LoanAmount           3.420195\n",
       "Loan_Amount_Term     2.117264\n",
       "Credit_History       8.143322\n",
       "Property_Area        0.000000\n",
       "Loan_Status          0.000000\n",
       "dtype: float64"
      ]
     },
     "execution_count": 33,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "## 9. Feature Scaling\n",
    "data.isnull().sum()*100/len(data)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 34,
   "id": "34ee7523",
   "metadata": {},
   "outputs": [],
   "source": [
    "data=data.drop('Loan_ID',axis=1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 35,
   "id": "3002f6c6",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Gender</th>\n",
       "      <th>Married</th>\n",
       "      <th>Dependents</th>\n",
       "      <th>Education</th>\n",
       "      <th>Self_Employed</th>\n",
       "      <th>ApplicantIncome</th>\n",
       "      <th>CoapplicantIncome</th>\n",
       "      <th>LoanAmount</th>\n",
       "      <th>Loan_Amount_Term</th>\n",
       "      <th>Credit_History</th>\n",
       "      <th>Property_Area</th>\n",
       "      <th>Loan_Status</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Male</td>\n",
       "      <td>No</td>\n",
       "      <td>0</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>5849</td>\n",
       "      <td>0.0</td>\n",
       "      <td>120.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Urban</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "  Gender Married Dependents Education Self_Employed  ApplicantIncome  \\\n",
       "0   Male      No          0  Graduate            No             5849   \n",
       "\n",
       "   CoapplicantIncome  LoanAmount  Loan_Amount_Term  Credit_History  \\\n",
       "0                0.0       120.0             360.0             1.0   \n",
       "\n",
       "  Property_Area Loan_Status  \n",
       "0         Urban           Y  "
      ]
     },
     "execution_count": 35,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data.head(1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 36,
   "id": "ec0a67d6",
   "metadata": {},
   "outputs": [],
   "source": [
    "columns=['Gender','Dependents','LoanAmount','Loan_Amount_Term']"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 37,
   "id": "37a5efdd",
   "metadata": {},
   "outputs": [],
   "source": [
    "data=data.dropna(subset=columns)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 38,
   "id": "2a4a3da2",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Gender               0.000000\n",
       "Married              0.000000\n",
       "Dependents           0.000000\n",
       "Education            0.000000\n",
       "Self_Employed        1.038062\n",
       "ApplicantIncome      0.000000\n",
       "CoapplicantIncome    0.000000\n",
       "LoanAmount           0.000000\n",
       "Loan_Amount_Term     0.000000\n",
       "Credit_History       8.477509\n",
       "Property_Area        0.000000\n",
       "Loan_Status          0.000000\n",
       "dtype: float64"
      ]
     },
     "execution_count": 38,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data.isnull().sum()*100/len(data)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 39,
   "id": "fc689483",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "'No'"
      ]
     },
     "execution_count": 39,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data['Self_Employed'].mode()[0]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 40,
   "id": "fdac0793",
   "metadata": {},
   "outputs": [],
   "source": [
    "data['Self_Employed']=data['Self_Employed'].fillna(data['Self_Employed'].mode()[0])\n",
    "data['Gender']=data['Gender'].fillna(data['Gender'].mode()[0])\n",
    "data['Married']=data['Married'].fillna(data['Married'].mode()[0])\n",
    "data['Dependents']=data['Dependents'].fillna(data['Dependents'].mode()[0])\n",
    "data['Education']=data['Education'].fillna(data['Education'].mode()[0])\n",
    "data['Self_Employed']=data['Self_Employed'].fillna(data['Self_Employed'].mode()[0])\n",
    "data['ApplicantIncome']=data['ApplicantIncome'].fillna(data['ApplicantIncome'].mode()[0])\n",
    "data['CoapplicantIncome']=data['CoapplicantIncome'].fillna(data['CoapplicantIncome'].mode()[0])\n",
    "data['LoanAmount']=data['LoanAmount'].fillna(data['LoanAmount'].mode()[0])\n",
    "data['Loan_Amount_Term']=data['Loan_Amount_Term'].fillna(data['Loan_Amount_Term'].mode()[0])\n",
    "data['Credit_History']=data['Credit_History'].fillna(data['Credit_History'].mode()[0])\n",
    "data['Loan_Amount_Term']=data['Loan_Amount_Term'].fillna(data['Loan_Amount_Term'].mode()[0])\n",
    "data['Credit_History']=data['Credit_History'].fillna(data['Credit_History'].mode()[0])\n",
    "data['Property_Area']=data['Property_Area'].fillna(data['Property_Area'].mode()[0])\n",
    "data['Loan_Status']=data['Loan_Status'].fillna(data['Loan_Status'].mode()[0])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 41,
   "id": "4e471da2",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Gender               0.0\n",
       "Married              0.0\n",
       "Dependents           0.0\n",
       "Education            0.0\n",
       "Self_Employed        0.0\n",
       "ApplicantIncome      0.0\n",
       "CoapplicantIncome    0.0\n",
       "LoanAmount           0.0\n",
       "Loan_Amount_Term     0.0\n",
       "Credit_History       0.0\n",
       "Property_Area        0.0\n",
       "Loan_Status          0.0\n",
       "dtype: float64"
      ]
     },
     "execution_count": 41,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data.isnull().sum()*100/len(data)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 42,
   "id": "67c7b312",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array(['Male', 'Female'], dtype=object)"
      ]
     },
     "execution_count": 42,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data['Gender'].unique()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 43,
   "id": "44746e95",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array(['No', 'Yes'], dtype=object)"
      ]
     },
     "execution_count": 43,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data['Self_Employed'].unique()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 44,
   "id": "eeed0f38",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "1.0"
      ]
     },
     "execution_count": 44,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data['Credit_History'].mode()[0]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 45,
   "id": "ffb58aa3",
   "metadata": {},
   "outputs": [],
   "source": [
    "data['Credit_History']=data['Credit_History'].fillna(data['Credit_History'].mode()[0])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 46,
   "id": "782a112e",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Gender               0.0\n",
       "Married              0.0\n",
       "Dependents           0.0\n",
       "Education            0.0\n",
       "Self_Employed        0.0\n",
       "ApplicantIncome      0.0\n",
       "CoapplicantIncome    0.0\n",
       "LoanAmount           0.0\n",
       "Loan_Amount_Term     0.0\n",
       "Credit_History       0.0\n",
       "Property_Area        0.0\n",
       "Loan_Status          0.0\n",
       "dtype: float64"
      ]
     },
     "execution_count": 46,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data.isnull().sum()*100/len(data)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 47,
   "id": "7a6cd4a5",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Gender</th>\n",
       "      <th>Married</th>\n",
       "      <th>Dependents</th>\n",
       "      <th>Education</th>\n",
       "      <th>Self_Employed</th>\n",
       "      <th>ApplicantIncome</th>\n",
       "      <th>CoapplicantIncome</th>\n",
       "      <th>LoanAmount</th>\n",
       "      <th>Loan_Amount_Term</th>\n",
       "      <th>Credit_History</th>\n",
       "      <th>Property_Area</th>\n",
       "      <th>Loan_Status</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>587</th>\n",
       "      <td>Female</td>\n",
       "      <td>No</td>\n",
       "      <td>0</td>\n",
       "      <td>Not Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>2165</td>\n",
       "      <td>0.0</td>\n",
       "      <td>70.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Semiurban</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>420</th>\n",
       "      <td>Male</td>\n",
       "      <td>Yes</td>\n",
       "      <td>0</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>5829</td>\n",
       "      <td>0.0</td>\n",
       "      <td>138.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Rural</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>488</th>\n",
       "      <td>Male</td>\n",
       "      <td>Yes</td>\n",
       "      <td>2</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>Yes</td>\n",
       "      <td>4583</td>\n",
       "      <td>2083.0</td>\n",
       "      <td>160.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Semiurban</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>82</th>\n",
       "      <td>Female</td>\n",
       "      <td>Yes</td>\n",
       "      <td>2</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>No</td>\n",
       "      <td>1378</td>\n",
       "      <td>1881.0</td>\n",
       "      <td>167.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Urban</td>\n",
       "      <td>N</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>594</th>\n",
       "      <td>Male</td>\n",
       "      <td>Yes</td>\n",
       "      <td>0</td>\n",
       "      <td>Graduate</td>\n",
       "      <td>Yes</td>\n",
       "      <td>16120</td>\n",
       "      <td>0.0</td>\n",
       "      <td>260.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>Urban</td>\n",
       "      <td>Y</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "     Gender Married Dependents     Education Self_Employed  ApplicantIncome  \\\n",
       "587  Female      No          0  Not Graduate            No             2165   \n",
       "420    Male     Yes          0      Graduate            No             5829   \n",
       "488    Male     Yes          2      Graduate           Yes             4583   \n",
       "82   Female     Yes          2      Graduate            No             1378   \n",
       "594    Male     Yes          0      Graduate           Yes            16120   \n",
       "\n",
       "     CoapplicantIncome  LoanAmount  Loan_Amount_Term  Credit_History  \\\n",
       "587                0.0        70.0             360.0             1.0   \n",
       "420                0.0       138.0             360.0             1.0   \n",
       "488             2083.0       160.0             360.0             1.0   \n",
       "82              1881.0       167.0             360.0             1.0   \n",
       "594                0.0       260.0             360.0             1.0   \n",
       "\n",
       "    Property_Area Loan_Status  \n",
       "587     Semiurban           Y  \n",
       "420         Rural           Y  \n",
       "488     Semiurban           Y  \n",
       "82          Urban           N  \n",
       "594         Urban           Y  "
      ]
     },
     "execution_count": 47,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data.sample(5)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 48,
   "id": "cd44695b",
   "metadata": {},
   "outputs": [],
   "source": [
    "data['Dependents']=data['Dependents'].replace(to_replace=\"3+\", value='4')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 49,
   "id": "f2ba9cb6",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array(['0', '1', '2', '4'], dtype=object)"
      ]
     },
     "execution_count": 49,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data['Dependents'].unique()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 50,
   "id": "1b8c442a",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array(['Y', 'N'], dtype=object)"
      ]
     },
     "execution_count": 50,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data['Loan_Status'].unique()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 51,
   "id": "8d02a22b",
   "metadata": {},
   "outputs": [],
   "source": [
    "# data['Gender']=data['Gender'].map({'Male':1,'Female':0}).astype(float)\n",
    "# data['Married']=data['Married'].map({'Yes':1, 'No':0})\n",
    "# data['Education']=data['Education'].map({'Graduate':1, 'Not Graduate':0})\n",
    "# data['Self_Employed']=data['Self_Employed'].map({'Yes':1, 'No':0})\n",
    "# data['Property_Area']=data['Property_Area'].map({'Rural':0, 'urban':1, 'Semiurban':2})\n",
    "# data['Loan_Status']=data['Loan_Status'].map({'Y':1, 'N':0})"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 54,
   "id": "1ca720f6",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Gender</th>\n",
       "      <th>Married</th>\n",
       "      <th>Education</th>\n",
       "      <th>Self_Employed</th>\n",
       "      <th>Dependents</th>\n",
       "      <th>ApplicantIncome</th>\n",
       "      <th>CoapplicantIncome</th>\n",
       "      <th>LoanAmount</th>\n",
       "      <th>Loan_Amount_Term</th>\n",
       "      <th>Credit_History</th>\n",
       "      <th>Property_Area</th>\n",
       "      <th>Loan_Status</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>5849</td>\n",
       "      <td>0.0</td>\n",
       "      <td>120.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>4583</td>\n",
       "      <td>1508.0</td>\n",
       "      <td>128.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>3000</td>\n",
       "      <td>0.0</td>\n",
       "      <td>66.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>2583</td>\n",
       "      <td>2358.0</td>\n",
       "      <td>120.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>6000</td>\n",
       "      <td>0.0</td>\n",
       "      <td>141.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>434</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>3750</td>\n",
       "      <td>0.0</td>\n",
       "      <td>100.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>436</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>1926</td>\n",
       "      <td>1851.0</td>\n",
       "      <td>50.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>438</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>10416</td>\n",
       "      <td>0.0</td>\n",
       "      <td>187.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>0.0</td>\n",
       "      <td>2</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>439</th>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>7142</td>\n",
       "      <td>0.0</td>\n",
       "      <td>138.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>440</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>3660</td>\n",
       "      <td>5064.0</td>\n",
       "      <td>187.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>410 rows × 12 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "     Gender  Married  Education  Self_Employed Dependents  ApplicantIncome  \\\n",
       "0         1        0          1              0          0             5849   \n",
       "1         1        1          1              0          1             4583   \n",
       "2         1        1          1              1          0             3000   \n",
       "3         1        1          0              0          0             2583   \n",
       "4         1        0          1              0          0             6000   \n",
       "..      ...      ...        ...            ...        ...              ...   \n",
       "434       1        0          1              0          0             3750   \n",
       "436       1        0          1              0          0             1926   \n",
       "438       1        0          1              1          0            10416   \n",
       "439       0        1          0              1          0             7142   \n",
       "440       1        0          1              0          0             3660   \n",
       "\n",
       "     CoapplicantIncome  LoanAmount  Loan_Amount_Term  Credit_History  \\\n",
       "0                  0.0       120.0             360.0             1.0   \n",
       "1               1508.0       128.0             360.0             1.0   \n",
       "2                  0.0        66.0             360.0             1.0   \n",
       "3               2358.0       120.0             360.0             1.0   \n",
       "4                  0.0       141.0             360.0             1.0   \n",
       "..                 ...         ...               ...             ...   \n",
       "434                0.0       100.0             360.0             1.0   \n",
       "436             1851.0        50.0             360.0             1.0   \n",
       "438                0.0       187.0             360.0             0.0   \n",
       "439                0.0       138.0             360.0             1.0   \n",
       "440             5064.0       187.0             360.0             1.0   \n",
       "\n",
       "     Property_Area  Loan_Status  \n",
       "0                2            1  \n",
       "1                2            0  \n",
       "2                2            1  \n",
       "3                2            1  \n",
       "4                2            1  \n",
       "..             ...          ...  \n",
       "434              1            1  \n",
       "436              1            1  \n",
       "438              2            0  \n",
       "439              2            1  \n",
       "440              1            1  \n",
       "\n",
       "[410 rows x 12 columns]"
      ]
     },
     "execution_count": 54,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "gender_new_data=[]\n",
    "married_new_data=[]\n",
    "education_new_data=[]\n",
    "self_employed_new_data=[]\n",
    "property_area_new_data=[]\n",
    "loan_status_new_data=[]\n",
    "for i in data['Gender'].values:\n",
    "    if i == 'Male':\n",
    "        gender_new_data.append(1)\n",
    "    elif i == 'Female':\n",
    "        gender_new_data.append(0) \n",
    "        \n",
    "for i in data['Married'].values:\n",
    "    if i == 'Yes':\n",
    "        married_new_data.append(1)\n",
    "    elif i == 'No':\n",
    "        married_new_data.append(0) \n",
    "        \n",
    "for i in data['Education'].values:\n",
    "    if i == 'Graduate':\n",
    "        education_new_data.append(1)\n",
    "    elif i == 'Not Graduate':\n",
    "        education_new_data.append(0) \n",
    "        \n",
    "for i in data['Self_Employed'].values:\n",
    "    if i == 'Yes':\n",
    "        self_employed_new_data.append(1)\n",
    "    elif i == 'No':\n",
    "        self_employed_new_data.append(0) \n",
    "        \n",
    "for i in data['Property_Area'].values:\n",
    "    if i == 'Rural':\n",
    "        gender_new_data.append(0)\n",
    "    elif i == 'Semiurban':\n",
    "        property_area_new_data.append(1) \n",
    "    elif i == 'Urban':\n",
    "        property_area_new_data.append(2)\n",
    "        \n",
    "for i in data['Loan_Status'].values:\n",
    "    if i == 'Y':\n",
    "        loan_status_new_data.append(1)\n",
    "    elif i == 'N':\n",
    "        loan_status_new_data.append(0)\n",
    "\n",
    "gender_new_data=gender_new_data[:410]\n",
    "married_new_data=married_new_data[:410]\n",
    "education_new_data=education_new_data[:410]\n",
    "self_employed_new_data=self_employed_new_data[:410]\n",
    "loan_status_new_data=loan_status_new_data[:410]\n",
    "\n",
    "        \n",
    "# print(len(gender_new_data))\n",
    "# print(len(married_new_data))\n",
    "# print(len(education_new_data))\n",
    "# print(len(self_employed_new_data))\n",
    "# print(len(property_area_new_data))\n",
    "# print(len(loan_status_new_data))\n",
    "data1=pd.DataFrame({'Gender':gender_new_data, 'Married':married_new_data, 'Education':education_new_data, 'Self_Employed':self_employed_new_data, 'Dependents':data['Dependents'][:410], 'ApplicantIncome':data['ApplicantIncome'][:410], 'CoapplicantIncome':data['CoapplicantIncome'][:410], 'LoanAmount':data['LoanAmount'][:410], 'Loan_Amount_Term':data['Loan_Amount_Term'][:410], 'Credit_History':data['Credit_History'][:410], 'Property_Area':property_area_new_data, 'Loan_Status':loan_status_new_data})\n",
    "data1"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 55,
   "id": "be7230b6",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Gender</th>\n",
       "      <th>Married</th>\n",
       "      <th>Education</th>\n",
       "      <th>Self_Employed</th>\n",
       "      <th>Dependents</th>\n",
       "      <th>ApplicantIncome</th>\n",
       "      <th>CoapplicantIncome</th>\n",
       "      <th>LoanAmount</th>\n",
       "      <th>Loan_Amount_Term</th>\n",
       "      <th>Credit_History</th>\n",
       "      <th>Property_Area</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>5849</td>\n",
       "      <td>0.0</td>\n",
       "      <td>120.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>4583</td>\n",
       "      <td>1508.0</td>\n",
       "      <td>128.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>3000</td>\n",
       "      <td>0.0</td>\n",
       "      <td>66.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>2583</td>\n",
       "      <td>2358.0</td>\n",
       "      <td>120.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>6000</td>\n",
       "      <td>0.0</td>\n",
       "      <td>141.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>434</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>3750</td>\n",
       "      <td>0.0</td>\n",
       "      <td>100.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>436</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>1926</td>\n",
       "      <td>1851.0</td>\n",
       "      <td>50.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>438</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>10416</td>\n",
       "      <td>0.0</td>\n",
       "      <td>187.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>0.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>439</th>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>7142</td>\n",
       "      <td>0.0</td>\n",
       "      <td>138.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>440</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>3660</td>\n",
       "      <td>5064.0</td>\n",
       "      <td>187.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>410 rows × 11 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "     Gender  Married  Education  Self_Employed Dependents  ApplicantIncome  \\\n",
       "0         1        0          1              0          0             5849   \n",
       "1         1        1          1              0          1             4583   \n",
       "2         1        1          1              1          0             3000   \n",
       "3         1        1          0              0          0             2583   \n",
       "4         1        0          1              0          0             6000   \n",
       "..      ...      ...        ...            ...        ...              ...   \n",
       "434       1        0          1              0          0             3750   \n",
       "436       1        0          1              0          0             1926   \n",
       "438       1        0          1              1          0            10416   \n",
       "439       0        1          0              1          0             7142   \n",
       "440       1        0          1              0          0             3660   \n",
       "\n",
       "     CoapplicantIncome  LoanAmount  Loan_Amount_Term  Credit_History  \\\n",
       "0                  0.0       120.0             360.0             1.0   \n",
       "1               1508.0       128.0             360.0             1.0   \n",
       "2                  0.0        66.0             360.0             1.0   \n",
       "3               2358.0       120.0             360.0             1.0   \n",
       "4                  0.0       141.0             360.0             1.0   \n",
       "..                 ...         ...               ...             ...   \n",
       "434                0.0       100.0             360.0             1.0   \n",
       "436             1851.0        50.0             360.0             1.0   \n",
       "438                0.0       187.0             360.0             0.0   \n",
       "439                0.0       138.0             360.0             1.0   \n",
       "440             5064.0       187.0             360.0             1.0   \n",
       "\n",
       "     Property_Area  \n",
       "0                2  \n",
       "1                2  \n",
       "2                2  \n",
       "3                2  \n",
       "4                2  \n",
       "..             ...  \n",
       "434              1  \n",
       "436              1  \n",
       "438              2  \n",
       "439              2  \n",
       "440              1  \n",
       "\n",
       "[410 rows x 11 columns]"
      ]
     },
     "execution_count": 55,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "X=data1.drop('Loan_Status', axis=1)\n",
    "y=data1['Loan_Status']\n",
    "X"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 56,
   "id": "1ecb36d5",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Gender</th>\n",
       "      <th>Married</th>\n",
       "      <th>Education</th>\n",
       "      <th>Self_Employed</th>\n",
       "      <th>Dependents</th>\n",
       "      <th>ApplicantIncome</th>\n",
       "      <th>CoapplicantIncome</th>\n",
       "      <th>LoanAmount</th>\n",
       "      <th>Loan_Amount_Term</th>\n",
       "      <th>Credit_History</th>\n",
       "      <th>Property_Area</th>\n",
       "      <th>Loan_Status</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>5849</td>\n",
       "      <td>0.0</td>\n",
       "      <td>120.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>4583</td>\n",
       "      <td>1508.0</td>\n",
       "      <td>128.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>3000</td>\n",
       "      <td>0.0</td>\n",
       "      <td>66.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>2583</td>\n",
       "      <td>2358.0</td>\n",
       "      <td>120.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>6000</td>\n",
       "      <td>0.0</td>\n",
       "      <td>141.0</td>\n",
       "      <td>360.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Gender  Married  Education  Self_Employed Dependents  ApplicantIncome  \\\n",
       "0       1        0          1              0          0             5849   \n",
       "1       1        1          1              0          1             4583   \n",
       "2       1        1          1              1          0             3000   \n",
       "3       1        1          0              0          0             2583   \n",
       "4       1        0          1              0          0             6000   \n",
       "\n",
       "   CoapplicantIncome  LoanAmount  Loan_Amount_Term  Credit_History  \\\n",
       "0                0.0       120.0             360.0             1.0   \n",
       "1             1508.0       128.0             360.0             1.0   \n",
       "2                0.0        66.0             360.0             1.0   \n",
       "3             2358.0       120.0             360.0             1.0   \n",
       "4                0.0       141.0             360.0             1.0   \n",
       "\n",
       "   Property_Area  Loan_Status  \n",
       "0              2            1  \n",
       "1              2            0  \n",
       "2              2            1  \n",
       "3              2            1  \n",
       "4              2            1  "
      ]
     },
     "execution_count": 56,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "data1.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 57,
   "id": "39b3f15b",
   "metadata": {},
   "outputs": [],
   "source": [
    "##Training Model Columns\n",
    "cols=['ApplicantIncome', 'CoapplicantIncome', 'LoanAmount', 'Loan_Amount_Term']"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 58,
   "id": "2eb2ff69",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Gender</th>\n",
       "      <th>Married</th>\n",
       "      <th>Education</th>\n",
       "      <th>Self_Employed</th>\n",
       "      <th>Dependents</th>\n",
       "      <th>ApplicantIncome</th>\n",
       "      <th>CoapplicantIncome</th>\n",
       "      <th>LoanAmount</th>\n",
       "      <th>Loan_Amount_Term</th>\n",
       "      <th>Credit_History</th>\n",
       "      <th>Property_Area</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0.056283</td>\n",
       "      <td>-0.689515</td>\n",
       "      <td>-0.296630</td>\n",
       "      <td>0.257486</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>-0.131102</td>\n",
       "      <td>-0.017869</td>\n",
       "      <td>-0.203024</td>\n",
       "      <td>0.257486</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>-0.365407</td>\n",
       "      <td>-0.689515</td>\n",
       "      <td>-0.928474</td>\n",
       "      <td>0.257486</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>-0.427129</td>\n",
       "      <td>0.360712</td>\n",
       "      <td>-0.296630</td>\n",
       "      <td>0.257486</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>0.078633</td>\n",
       "      <td>-0.689515</td>\n",
       "      <td>-0.050913</td>\n",
       "      <td>0.257486</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>434</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>-0.254397</td>\n",
       "      <td>-0.689515</td>\n",
       "      <td>-0.530646</td>\n",
       "      <td>0.257486</td>\n",
       "      <td>1.0</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>436</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>-0.524374</td>\n",
       "      <td>0.134900</td>\n",
       "      <td>-1.115688</td>\n",
       "      <td>0.257486</td>\n",
       "      <td>1.0</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>438</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0.732261</td>\n",
       "      <td>-0.689515</td>\n",
       "      <td>0.487325</td>\n",
       "      <td>0.257486</td>\n",
       "      <td>0.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>439</th>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0.247665</td>\n",
       "      <td>-0.689515</td>\n",
       "      <td>-0.086015</td>\n",
       "      <td>0.257486</td>\n",
       "      <td>1.0</td>\n",
       "      <td>2</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>440</th>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>-0.267718</td>\n",
       "      <td>1.565933</td>\n",
       "      <td>0.487325</td>\n",
       "      <td>0.257486</td>\n",
       "      <td>1.0</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>410 rows × 11 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "     Gender  Married  Education  Self_Employed Dependents  ApplicantIncome  \\\n",
       "0         1        0          1              0          0         0.056283   \n",
       "1         1        1          1              0          1        -0.131102   \n",
       "2         1        1          1              1          0        -0.365407   \n",
       "3         1        1          0              0          0        -0.427129   \n",
       "4         1        0          1              0          0         0.078633   \n",
       "..      ...      ...        ...            ...        ...              ...   \n",
       "434       1        0          1              0          0        -0.254397   \n",
       "436       1        0          1              0          0        -0.524374   \n",
       "438       1        0          1              1          0         0.732261   \n",
       "439       0        1          0              1          0         0.247665   \n",
       "440       1        0          1              0          0        -0.267718   \n",
       "\n",
       "     CoapplicantIncome  LoanAmount  Loan_Amount_Term  Credit_History  \\\n",
       "0            -0.689515   -0.296630          0.257486             1.0   \n",
       "1            -0.017869   -0.203024          0.257486             1.0   \n",
       "2            -0.689515   -0.928474          0.257486             1.0   \n",
       "3             0.360712   -0.296630          0.257486             1.0   \n",
       "4            -0.689515   -0.050913          0.257486             1.0   \n",
       "..                 ...         ...               ...             ...   \n",
       "434          -0.689515   -0.530646          0.257486             1.0   \n",
       "436           0.134900   -1.115688          0.257486             1.0   \n",
       "438          -0.689515    0.487325          0.257486             0.0   \n",
       "439          -0.689515   -0.086015          0.257486             1.0   \n",
       "440           1.565933    0.487325          0.257486             1.0   \n",
       "\n",
       "     Property_Area  \n",
       "0                2  \n",
       "1                2  \n",
       "2                2  \n",
       "3                2  \n",
       "4                2  \n",
       "..             ...  \n",
       "434              1  \n",
       "436              1  \n",
       "438              2  \n",
       "439              2  \n",
       "440              1  \n",
       "\n",
       "[410 rows x 11 columns]"
      ]
     },
     "execution_count": 58,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "from sklearn.preprocessing import StandardScaler\n",
    "st=StandardScaler()\n",
    "X[cols]=st.fit_transform(X[cols])\n",
    "X"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 59,
   "id": "d5bc9bb8",
   "metadata": {},
   "outputs": [],
   "source": [
    "## 10. Splitting The Dataset Into The Training Set And Test Set & Applying K-Fold Cross Validation\n",
    "from sklearn.model_selection import train_test_split\n",
    "from sklearn.model_selection import cross_val_score\n",
    "from sklearn.metrics import accuracy_score\n",
    "import numpy as np"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 60,
   "id": "07e7a752",
   "metadata": {},
   "outputs": [],
   "source": [
    "model_df={}\n",
    "def model_val(model,X,y):\n",
    "    X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.20,random_state=42)\n",
    "    \n",
    "    model.fit(X_train, y_train)\n",
    "    y_pred=model.predict(X_test)\n",
    "    print(f\"{model} accuracy is {accuracy_score(y_test,y_pred)}\")\n",
    "    \n",
    "    score=cross_val_score(model,X,y,cv=5)\n",
    "    print(f'{model} Avg cross val score is {np.mean(score)}')\n",
    "    model_df[model]=round(np.mean(score)*100,2)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 61,
   "id": "e62481aa",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "{}"
      ]
     },
     "execution_count": 61,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "model_df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 62,
   "id": "a68a57ac",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "LogisticRegression() accuracy is 0.7682926829268293\n",
      "LogisticRegression() Avg cross val score is 0.7902439024390244\n"
     ]
    }
   ],
   "source": [
    "## Logistic Regression\n",
    "\n",
    "from sklearn.linear_model import LogisticRegression\n",
    "model=LogisticRegression()\n",
    "# print(accuracy_score(model))\n",
    "model_val(model,X,y)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 63,
   "id": "e37b06b2",
   "metadata": {},
   "outputs": [],
   "source": [
    "## SVC\n",
    "\n",
    "from sklearn import svm\n",
    "model=svm.SVC()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 64,
   "id": "25618905",
   "metadata": {},
   "outputs": [],
   "source": [
    "## Decision Tree Classifier\n",
    "\n",
    "from sklearn.tree import DecisionTreeClassifier\n",
    "model = DecisionTreeClassifier()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 65,
   "id": "7a9bd0d0",
   "metadata": {},
   "outputs": [],
   "source": [
    "## Hyperparameter Tuning\n",
    "\n",
    "from sklearn.model_selection import RandomizedSearchCV"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 66,
   "id": "76c8c063",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Fitting 5 folds for each of 20 candidates, totalling 100 fits\n"
     ]
    },
    {
     "data": {
      "text/html": [
       "<style>#sk-container-id-1 {color: black;}#sk-container-id-1 pre{padding: 0;}#sk-container-id-1 div.sk-toggleable {background-color: white;}#sk-container-id-1 label.sk-toggleable__label {cursor: pointer;display: block;width: 100%;margin-bottom: 0;padding: 0.3em;box-sizing: border-box;text-align: center;}#sk-container-id-1 label.sk-toggleable__label-arrow:before {content: \"▸\";float: left;margin-right: 0.25em;color: #696969;}#sk-container-id-1 label.sk-toggleable__label-arrow:hover:before {color: black;}#sk-container-id-1 div.sk-estimator:hover label.sk-toggleable__label-arrow:before {color: black;}#sk-container-id-1 div.sk-toggleable__content {max-height: 0;max-width: 0;overflow: hidden;text-align: left;background-color: #f0f8ff;}#sk-container-id-1 div.sk-toggleable__content pre {margin: 0.2em;color: black;border-radius: 0.25em;background-color: #f0f8ff;}#sk-container-id-1 input.sk-toggleable__control:checked~div.sk-toggleable__content {max-height: 200px;max-width: 100%;overflow: auto;}#sk-container-id-1 input.sk-toggleable__control:checked~label.sk-toggleable__label-arrow:before {content: \"▾\";}#sk-container-id-1 div.sk-estimator input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-1 div.sk-label input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-1 input.sk-hidden--visually {border: 0;clip: rect(1px 1px 1px 1px);clip: rect(1px, 1px, 1px, 1px);height: 1px;margin: -1px;overflow: hidden;padding: 0;position: absolute;width: 1px;}#sk-container-id-1 div.sk-estimator {font-family: monospace;background-color: #f0f8ff;border: 1px dotted black;border-radius: 0.25em;box-sizing: border-box;margin-bottom: 0.5em;}#sk-container-id-1 div.sk-estimator:hover {background-color: #d4ebff;}#sk-container-id-1 div.sk-parallel-item::after {content: \"\";width: 100%;border-bottom: 1px solid gray;flex-grow: 1;}#sk-container-id-1 div.sk-label:hover label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-1 div.sk-serial::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: 0;}#sk-container-id-1 div.sk-serial {display: flex;flex-direction: column;align-items: center;background-color: white;padding-right: 0.2em;padding-left: 0.2em;position: relative;}#sk-container-id-1 div.sk-item {position: relative;z-index: 1;}#sk-container-id-1 div.sk-parallel {display: flex;align-items: stretch;justify-content: center;background-color: white;position: relative;}#sk-container-id-1 div.sk-item::before, #sk-container-id-1 div.sk-parallel-item::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: -1;}#sk-container-id-1 div.sk-parallel-item {display: flex;flex-direction: column;z-index: 1;position: relative;background-color: white;}#sk-container-id-1 div.sk-parallel-item:first-child::after {align-self: flex-end;width: 50%;}#sk-container-id-1 div.sk-parallel-item:last-child::after {align-self: flex-start;width: 50%;}#sk-container-id-1 div.sk-parallel-item:only-child::after {width: 0;}#sk-container-id-1 div.sk-dashed-wrapped {border: 1px dashed gray;margin: 0 0.4em 0.5em 0.4em;box-sizing: border-box;padding-bottom: 0.4em;background-color: white;}#sk-container-id-1 div.sk-label label {font-family: monospace;font-weight: bold;display: inline-block;line-height: 1.2em;}#sk-container-id-1 div.sk-label-container {text-align: center;}#sk-container-id-1 div.sk-container {/* jupyter's `normalize.less` sets `[hidden] { display: none; }` but bootstrap.min.css set `[hidden] { display: none !important; }` so we also need the `!important` here to be able to override the default hidden behavior on the sphinx rendered scikit-learn.org. See: https://github.com/scikit-learn/scikit-learn/issues/21755 */display: inline-block !important;position: relative;}#sk-container-id-1 div.sk-text-repr-fallback {display: none;}</style><div id=\"sk-container-id-1\" class=\"sk-top-container\"><div class=\"sk-text-repr-fallback\"><pre>RandomizedSearchCV(cv=5, estimator=LogisticRegression(), n_iter=20,\n",
       "                   param_distributions={&#x27;C&#x27;: array([1.00000000e-04, 2.63665090e-04, 6.95192796e-04, 1.83298071e-03,\n",
       "       4.83293024e-03, 1.27427499e-02, 3.35981829e-02, 8.85866790e-02,\n",
       "       2.33572147e-01, 6.15848211e-01, 1.62377674e+00, 4.28133240e+00,\n",
       "       1.12883789e+01, 2.97635144e+01, 7.84759970e+01, 2.06913808e+02,\n",
       "       5.45559478e+02, 1.43844989e+03, 3.79269019e+03, 1.00000000e+04]),\n",
       "                                        &#x27;solver&#x27;: [&#x27;liblinear&#x27;]},\n",
       "                   verbose=True)</pre><b>In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook. <br />On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.</b></div><div class=\"sk-container\" hidden><div class=\"sk-item sk-dashed-wrapped\"><div class=\"sk-label-container\"><div class=\"sk-label sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-1\" type=\"checkbox\" ><label for=\"sk-estimator-id-1\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">RandomizedSearchCV</label><div class=\"sk-toggleable__content\"><pre>RandomizedSearchCV(cv=5, estimator=LogisticRegression(), n_iter=20,\n",
       "                   param_distributions={&#x27;C&#x27;: array([1.00000000e-04, 2.63665090e-04, 6.95192796e-04, 1.83298071e-03,\n",
       "       4.83293024e-03, 1.27427499e-02, 3.35981829e-02, 8.85866790e-02,\n",
       "       2.33572147e-01, 6.15848211e-01, 1.62377674e+00, 4.28133240e+00,\n",
       "       1.12883789e+01, 2.97635144e+01, 7.84759970e+01, 2.06913808e+02,\n",
       "       5.45559478e+02, 1.43844989e+03, 3.79269019e+03, 1.00000000e+04]),\n",
       "                                        &#x27;solver&#x27;: [&#x27;liblinear&#x27;]},\n",
       "                   verbose=True)</pre></div></div></div><div class=\"sk-parallel\"><div class=\"sk-parallel-item\"><div class=\"sk-item\"><div class=\"sk-label-container\"><div class=\"sk-label sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-2\" type=\"checkbox\" ><label for=\"sk-estimator-id-2\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">estimator: LogisticRegression</label><div class=\"sk-toggleable__content\"><pre>LogisticRegression()</pre></div></div></div><div class=\"sk-serial\"><div class=\"sk-item\"><div class=\"sk-estimator sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-3\" type=\"checkbox\" ><label for=\"sk-estimator-id-3\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">LogisticRegression</label><div class=\"sk-toggleable__content\"><pre>LogisticRegression()</pre></div></div></div></div></div></div></div></div></div></div>"
      ],
      "text/plain": [
       "RandomizedSearchCV(cv=5, estimator=LogisticRegression(), n_iter=20,\n",
       "                   param_distributions={'C': array([1.00000000e-04, 2.63665090e-04, 6.95192796e-04, 1.83298071e-03,\n",
       "       4.83293024e-03, 1.27427499e-02, 3.35981829e-02, 8.85866790e-02,\n",
       "       2.33572147e-01, 6.15848211e-01, 1.62377674e+00, 4.28133240e+00,\n",
       "       1.12883789e+01, 2.97635144e+01, 7.84759970e+01, 2.06913808e+02,\n",
       "       5.45559478e+02, 1.43844989e+03, 3.79269019e+03, 1.00000000e+04]),\n",
       "                                        'solver': ['liblinear']},\n",
       "                   verbose=True)"
      ]
     },
     "execution_count": 66,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Logistic Regression\n",
    "\n",
    "log_reg_grid={\"C\":np.logspace(-4,4,20),\n",
    "             \"solver\":['liblinear']}\n",
    "\n",
    "rs_log_reg=RandomizedSearchCV(LogisticRegression(), param_distributions=log_reg_grid,\n",
    "                             n_iter=20, cv=5, verbose=True)\n",
    "\n",
    "rs_log_reg.fit(X,y)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 67,
   "id": "771eb983",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0.7902439024390244"
      ]
     },
     "execution_count": 67,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rs_log_reg.best_score_"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 68,
   "id": "ffadfc26",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "{'solver': 'liblinear', 'C': 0.23357214690901212}"
      ]
     },
     "execution_count": 68,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rs_log_reg.best_params_"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 69,
   "id": "9f24d9b0",
   "metadata": {},
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "C:\\Users\\DELL\\anaconda3\\Lib\\site-packages\\sklearn\\model_selection\\_search.py:307: UserWarning: The total space of parameters 4 is smaller than n_iter=20. Running 4 iterations. For exhaustive searches, use GridSearchCV.\n",
      "  warnings.warn(\n"
     ]
    },
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Fitting 5 folds for each of 4 candidates, totalling 20 fits\n"
     ]
    },
    {
     "data": {
      "text/html": [
       "<style>#sk-container-id-2 {color: black;}#sk-container-id-2 pre{padding: 0;}#sk-container-id-2 div.sk-toggleable {background-color: white;}#sk-container-id-2 label.sk-toggleable__label {cursor: pointer;display: block;width: 100%;margin-bottom: 0;padding: 0.3em;box-sizing: border-box;text-align: center;}#sk-container-id-2 label.sk-toggleable__label-arrow:before {content: \"▸\";float: left;margin-right: 0.25em;color: #696969;}#sk-container-id-2 label.sk-toggleable__label-arrow:hover:before {color: black;}#sk-container-id-2 div.sk-estimator:hover label.sk-toggleable__label-arrow:before {color: black;}#sk-container-id-2 div.sk-toggleable__content {max-height: 0;max-width: 0;overflow: hidden;text-align: left;background-color: #f0f8ff;}#sk-container-id-2 div.sk-toggleable__content pre {margin: 0.2em;color: black;border-radius: 0.25em;background-color: #f0f8ff;}#sk-container-id-2 input.sk-toggleable__control:checked~div.sk-toggleable__content {max-height: 200px;max-width: 100%;overflow: auto;}#sk-container-id-2 input.sk-toggleable__control:checked~label.sk-toggleable__label-arrow:before {content: \"▾\";}#sk-container-id-2 div.sk-estimator input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-2 div.sk-label input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-2 input.sk-hidden--visually {border: 0;clip: rect(1px 1px 1px 1px);clip: rect(1px, 1px, 1px, 1px);height: 1px;margin: -1px;overflow: hidden;padding: 0;position: absolute;width: 1px;}#sk-container-id-2 div.sk-estimator {font-family: monospace;background-color: #f0f8ff;border: 1px dotted black;border-radius: 0.25em;box-sizing: border-box;margin-bottom: 0.5em;}#sk-container-id-2 div.sk-estimator:hover {background-color: #d4ebff;}#sk-container-id-2 div.sk-parallel-item::after {content: \"\";width: 100%;border-bottom: 1px solid gray;flex-grow: 1;}#sk-container-id-2 div.sk-label:hover label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-2 div.sk-serial::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: 0;}#sk-container-id-2 div.sk-serial {display: flex;flex-direction: column;align-items: center;background-color: white;padding-right: 0.2em;padding-left: 0.2em;position: relative;}#sk-container-id-2 div.sk-item {position: relative;z-index: 1;}#sk-container-id-2 div.sk-parallel {display: flex;align-items: stretch;justify-content: center;background-color: white;position: relative;}#sk-container-id-2 div.sk-item::before, #sk-container-id-2 div.sk-parallel-item::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: -1;}#sk-container-id-2 div.sk-parallel-item {display: flex;flex-direction: column;z-index: 1;position: relative;background-color: white;}#sk-container-id-2 div.sk-parallel-item:first-child::after {align-self: flex-end;width: 50%;}#sk-container-id-2 div.sk-parallel-item:last-child::after {align-self: flex-start;width: 50%;}#sk-container-id-2 div.sk-parallel-item:only-child::after {width: 0;}#sk-container-id-2 div.sk-dashed-wrapped {border: 1px dashed gray;margin: 0 0.4em 0.5em 0.4em;box-sizing: border-box;padding-bottom: 0.4em;background-color: white;}#sk-container-id-2 div.sk-label label {font-family: monospace;font-weight: bold;display: inline-block;line-height: 1.2em;}#sk-container-id-2 div.sk-label-container {text-align: center;}#sk-container-id-2 div.sk-container {/* jupyter's `normalize.less` sets `[hidden] { display: none; }` but bootstrap.min.css set `[hidden] { display: none !important; }` so we also need the `!important` here to be able to override the default hidden behavior on the sphinx rendered scikit-learn.org. See: https://github.com/scikit-learn/scikit-learn/issues/21755 */display: inline-block !important;position: relative;}#sk-container-id-2 div.sk-text-repr-fallback {display: none;}</style><div id=\"sk-container-id-2\" class=\"sk-top-container\"><div class=\"sk-text-repr-fallback\"><pre>RandomizedSearchCV(cv=5, estimator=SVC(), n_iter=20,\n",
       "                   param_distributions={&#x27;C&#x27;: [0.25, 0.5, 0.75, 1],\n",
       "                                        &#x27;kernel&#x27;: [&#x27;linear&#x27;]},\n",
       "                   verbose=True)</pre><b>In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook. <br />On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.</b></div><div class=\"sk-container\" hidden><div class=\"sk-item sk-dashed-wrapped\"><div class=\"sk-label-container\"><div class=\"sk-label sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-4\" type=\"checkbox\" ><label for=\"sk-estimator-id-4\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">RandomizedSearchCV</label><div class=\"sk-toggleable__content\"><pre>RandomizedSearchCV(cv=5, estimator=SVC(), n_iter=20,\n",
       "                   param_distributions={&#x27;C&#x27;: [0.25, 0.5, 0.75, 1],\n",
       "                                        &#x27;kernel&#x27;: [&#x27;linear&#x27;]},\n",
       "                   verbose=True)</pre></div></div></div><div class=\"sk-parallel\"><div class=\"sk-parallel-item\"><div class=\"sk-item\"><div class=\"sk-label-container\"><div class=\"sk-label sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-5\" type=\"checkbox\" ><label for=\"sk-estimator-id-5\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">estimator: SVC</label><div class=\"sk-toggleable__content\"><pre>SVC()</pre></div></div></div><div class=\"sk-serial\"><div class=\"sk-item\"><div class=\"sk-estimator sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-6\" type=\"checkbox\" ><label for=\"sk-estimator-id-6\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">SVC</label><div class=\"sk-toggleable__content\"><pre>SVC()</pre></div></div></div></div></div></div></div></div></div></div>"
      ],
      "text/plain": [
       "RandomizedSearchCV(cv=5, estimator=SVC(), n_iter=20,\n",
       "                   param_distributions={'C': [0.25, 0.5, 0.75, 1],\n",
       "                                        'kernel': ['linear']},\n",
       "                   verbose=True)"
      ]
     },
     "execution_count": 69,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "## SVC\n",
    "\n",
    "svc_grid={'C':[0.25,0.50,0.75,1], \"kernel\":[\"linear\"]}\n",
    "\n",
    "rs_svc=RandomizedSearchCV(svm.SVC(), param_distributions=svc_grid, cv=5, n_iter=20, verbose=True)\n",
    "\n",
    "rs_svc.fit(X,y)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 70,
   "id": "20013d78",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0.8000000000000002"
      ]
     },
     "execution_count": 70,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rs_svc.best_score_"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 71,
   "id": "daa8ed4b",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "{'kernel': 'linear', 'C': 0.25}"
      ]
     },
     "execution_count": 71,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rs_svc.best_params_"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 72,
   "id": "379908fa",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "RandomForestClassifier() accuracy is 0.7317073170731707\n",
      "RandomForestClassifier() Avg cross val score is 0.7780487804878049\n"
     ]
    }
   ],
   "source": [
    "from sklearn.ensemble import RandomForestClassifier\n",
    "model =RandomForestClassifier()\n",
    "model_val(model,X,y)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 73,
   "id": "f5294866",
   "metadata": {},
   "outputs": [],
   "source": [
    "RandomForestClassifier()\n",
    "rf_grid={'n_estimators':np.arange(10,1000,10),\n",
    "        'max_features':['auto','sqrt'],\n",
    "        'max_depth':[None,3,5,10,20,30],\n",
    "        'min_samples_split':[2,5,20,50,100],\n",
    "        'min_samples_leaf':[1,2,5,10]\n",
    "        }"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 74,
   "id": "34ecd90a",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Fitting 5 folds for each of 20 candidates, totalling 100 fits\n"
     ]
    },
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "C:\\Users\\DELL\\anaconda3\\Lib\\site-packages\\sklearn\\model_selection\\_validation.py:425: FitFailedWarning: \n",
      "35 fits failed out of a total of 100.\n",
      "The score on these train-test partitions for these parameters will be set to nan.\n",
      "If these failures are not expected, you can try to debug them by setting error_score='raise'.\n",
      "\n",
      "Below are more details about the failures:\n",
      "--------------------------------------------------------------------------------\n",
      "35 fits failed with the following error:\n",
      "Traceback (most recent call last):\n",
      "  File \"C:\\Users\\DELL\\anaconda3\\Lib\\site-packages\\sklearn\\model_selection\\_validation.py\", line 732, in _fit_and_score\n",
      "    estimator.fit(X_train, y_train, **fit_params)\n",
      "  File \"C:\\Users\\DELL\\anaconda3\\Lib\\site-packages\\sklearn\\base.py\", line 1144, in wrapper\n",
      "    estimator._validate_params()\n",
      "  File \"C:\\Users\\DELL\\anaconda3\\Lib\\site-packages\\sklearn\\base.py\", line 637, in _validate_params\n",
      "    validate_parameter_constraints(\n",
      "  File \"C:\\Users\\DELL\\anaconda3\\Lib\\site-packages\\sklearn\\utils\\_param_validation.py\", line 95, in validate_parameter_constraints\n",
      "    raise InvalidParameterError(\n",
      "sklearn.utils._param_validation.InvalidParameterError: The 'max_features' parameter of RandomForestClassifier must be an int in the range [1, inf), a float in the range (0.0, 1.0], a str among {'sqrt', 'log2'} or None. Got 'auto' instead.\n",
      "\n",
      "  warnings.warn(some_fits_failed_message, FitFailedWarning)\n",
      "C:\\Users\\DELL\\anaconda3\\Lib\\site-packages\\sklearn\\model_selection\\_search.py:976: UserWarning: One or more of the test scores are non-finite: [0.8        0.79512195        nan 0.79512195        nan 0.8\n",
      "        nan 0.79756098 0.8               nan        nan        nan\n",
      " 0.7804878  0.8               nan 0.79756098 0.79756098 0.77804878\n",
      " 0.79756098 0.79512195]\n",
      "  warnings.warn(\n"
     ]
    },
    {
     "data": {
      "text/html": [
       "<style>#sk-container-id-3 {color: black;}#sk-container-id-3 pre{padding: 0;}#sk-container-id-3 div.sk-toggleable {background-color: white;}#sk-container-id-3 label.sk-toggleable__label {cursor: pointer;display: block;width: 100%;margin-bottom: 0;padding: 0.3em;box-sizing: border-box;text-align: center;}#sk-container-id-3 label.sk-toggleable__label-arrow:before {content: \"▸\";float: left;margin-right: 0.25em;color: #696969;}#sk-container-id-3 label.sk-toggleable__label-arrow:hover:before {color: black;}#sk-container-id-3 div.sk-estimator:hover label.sk-toggleable__label-arrow:before {color: black;}#sk-container-id-3 div.sk-toggleable__content {max-height: 0;max-width: 0;overflow: hidden;text-align: left;background-color: #f0f8ff;}#sk-container-id-3 div.sk-toggleable__content pre {margin: 0.2em;color: black;border-radius: 0.25em;background-color: #f0f8ff;}#sk-container-id-3 input.sk-toggleable__control:checked~div.sk-toggleable__content {max-height: 200px;max-width: 100%;overflow: auto;}#sk-container-id-3 input.sk-toggleable__control:checked~label.sk-toggleable__label-arrow:before {content: \"▾\";}#sk-container-id-3 div.sk-estimator input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-3 div.sk-label input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-3 input.sk-hidden--visually {border: 0;clip: rect(1px 1px 1px 1px);clip: rect(1px, 1px, 1px, 1px);height: 1px;margin: -1px;overflow: hidden;padding: 0;position: absolute;width: 1px;}#sk-container-id-3 div.sk-estimator {font-family: monospace;background-color: #f0f8ff;border: 1px dotted black;border-radius: 0.25em;box-sizing: border-box;margin-bottom: 0.5em;}#sk-container-id-3 div.sk-estimator:hover {background-color: #d4ebff;}#sk-container-id-3 div.sk-parallel-item::after {content: \"\";width: 100%;border-bottom: 1px solid gray;flex-grow: 1;}#sk-container-id-3 div.sk-label:hover label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-3 div.sk-serial::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: 0;}#sk-container-id-3 div.sk-serial {display: flex;flex-direction: column;align-items: center;background-color: white;padding-right: 0.2em;padding-left: 0.2em;position: relative;}#sk-container-id-3 div.sk-item {position: relative;z-index: 1;}#sk-container-id-3 div.sk-parallel {display: flex;align-items: stretch;justify-content: center;background-color: white;position: relative;}#sk-container-id-3 div.sk-item::before, #sk-container-id-3 div.sk-parallel-item::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: -1;}#sk-container-id-3 div.sk-parallel-item {display: flex;flex-direction: column;z-index: 1;position: relative;background-color: white;}#sk-container-id-3 div.sk-parallel-item:first-child::after {align-self: flex-end;width: 50%;}#sk-container-id-3 div.sk-parallel-item:last-child::after {align-self: flex-start;width: 50%;}#sk-container-id-3 div.sk-parallel-item:only-child::after {width: 0;}#sk-container-id-3 div.sk-dashed-wrapped {border: 1px dashed gray;margin: 0 0.4em 0.5em 0.4em;box-sizing: border-box;padding-bottom: 0.4em;background-color: white;}#sk-container-id-3 div.sk-label label {font-family: monospace;font-weight: bold;display: inline-block;line-height: 1.2em;}#sk-container-id-3 div.sk-label-container {text-align: center;}#sk-container-id-3 div.sk-container {/* jupyter's `normalize.less` sets `[hidden] { display: none; }` but bootstrap.min.css set `[hidden] { display: none !important; }` so we also need the `!important` here to be able to override the default hidden behavior on the sphinx rendered scikit-learn.org. See: https://github.com/scikit-learn/scikit-learn/issues/21755 */display: inline-block !important;position: relative;}#sk-container-id-3 div.sk-text-repr-fallback {display: none;}</style><div id=\"sk-container-id-3\" class=\"sk-top-container\"><div class=\"sk-text-repr-fallback\"><pre>RandomizedSearchCV(cv=5, estimator=RandomForestClassifier(), n_iter=20,\n",
       "                   param_distributions={&#x27;max_depth&#x27;: [None, 3, 5, 10, 20, 30],\n",
       "                                        &#x27;max_features&#x27;: [&#x27;auto&#x27;, &#x27;sqrt&#x27;],\n",
       "                                        &#x27;min_samples_leaf&#x27;: [1, 2, 5, 10],\n",
       "                                        &#x27;min_samples_split&#x27;: [2, 5, 20, 50,\n",
       "                                                              100],\n",
       "                                        &#x27;n_estimators&#x27;: array([ 10,  20,  30,  40,  50,  60,  70,  80,  90, 100, 110, 120, 130,\n",
       "       140, 150, 160, 170, 180, 190, 200, 210, 220, 230, 240, 250, 260,\n",
       "       270, 280, 290, 300, 310, 320, 330, 340, 350, 360, 370, 380, 390,\n",
       "       400, 410, 420, 430, 440, 450, 460, 470, 480, 490, 500, 510, 520,\n",
       "       530, 540, 550, 560, 570, 580, 590, 600, 610, 620, 630, 640, 650,\n",
       "       660, 670, 680, 690, 700, 710, 720, 730, 740, 750, 760, 770, 780,\n",
       "       790, 800, 810, 820, 830, 840, 850, 860, 870, 880, 890, 900, 910,\n",
       "       920, 930, 940, 950, 960, 970, 980, 990])},\n",
       "                   verbose=True)</pre><b>In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook. <br />On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.</b></div><div class=\"sk-container\" hidden><div class=\"sk-item sk-dashed-wrapped\"><div class=\"sk-label-container\"><div class=\"sk-label sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-7\" type=\"checkbox\" ><label for=\"sk-estimator-id-7\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">RandomizedSearchCV</label><div class=\"sk-toggleable__content\"><pre>RandomizedSearchCV(cv=5, estimator=RandomForestClassifier(), n_iter=20,\n",
       "                   param_distributions={&#x27;max_depth&#x27;: [None, 3, 5, 10, 20, 30],\n",
       "                                        &#x27;max_features&#x27;: [&#x27;auto&#x27;, &#x27;sqrt&#x27;],\n",
       "                                        &#x27;min_samples_leaf&#x27;: [1, 2, 5, 10],\n",
       "                                        &#x27;min_samples_split&#x27;: [2, 5, 20, 50,\n",
       "                                                              100],\n",
       "                                        &#x27;n_estimators&#x27;: array([ 10,  20,  30,  40,  50,  60,  70,  80,  90, 100, 110, 120, 130,\n",
       "       140, 150, 160, 170, 180, 190, 200, 210, 220, 230, 240, 250, 260,\n",
       "       270, 280, 290, 300, 310, 320, 330, 340, 350, 360, 370, 380, 390,\n",
       "       400, 410, 420, 430, 440, 450, 460, 470, 480, 490, 500, 510, 520,\n",
       "       530, 540, 550, 560, 570, 580, 590, 600, 610, 620, 630, 640, 650,\n",
       "       660, 670, 680, 690, 700, 710, 720, 730, 740, 750, 760, 770, 780,\n",
       "       790, 800, 810, 820, 830, 840, 850, 860, 870, 880, 890, 900, 910,\n",
       "       920, 930, 940, 950, 960, 970, 980, 990])},\n",
       "                   verbose=True)</pre></div></div></div><div class=\"sk-parallel\"><div class=\"sk-parallel-item\"><div class=\"sk-item\"><div class=\"sk-label-container\"><div class=\"sk-label sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-8\" type=\"checkbox\" ><label for=\"sk-estimator-id-8\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">estimator: RandomForestClassifier</label><div class=\"sk-toggleable__content\"><pre>RandomForestClassifier()</pre></div></div></div><div class=\"sk-serial\"><div class=\"sk-item\"><div class=\"sk-estimator sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-9\" type=\"checkbox\" ><label for=\"sk-estimator-id-9\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">RandomForestClassifier</label><div class=\"sk-toggleable__content\"><pre>RandomForestClassifier()</pre></div></div></div></div></div></div></div></div></div></div>"
      ],
      "text/plain": [
       "RandomizedSearchCV(cv=5, estimator=RandomForestClassifier(), n_iter=20,\n",
       "                   param_distributions={'max_depth': [None, 3, 5, 10, 20, 30],\n",
       "                                        'max_features': ['auto', 'sqrt'],\n",
       "                                        'min_samples_leaf': [1, 2, 5, 10],\n",
       "                                        'min_samples_split': [2, 5, 20, 50,\n",
       "                                                              100],\n",
       "                                        'n_estimators': array([ 10,  20,  30,  40,  50,  60,  70,  80,  90, 100, 110, 120, 130,\n",
       "       140, 150, 160, 170, 180, 190, 200, 210, 220, 230, 240, 250, 260,\n",
       "       270, 280, 290, 300, 310, 320, 330, 340, 350, 360, 370, 380, 390,\n",
       "       400, 410, 420, 430, 440, 450, 460, 470, 480, 490, 500, 510, 520,\n",
       "       530, 540, 550, 560, 570, 580, 590, 600, 610, 620, 630, 640, 650,\n",
       "       660, 670, 680, 690, 700, 710, 720, 730, 740, 750, 760, 770, 780,\n",
       "       790, 800, 810, 820, 830, 840, 850, 860, 870, 880, 890, 900, 910,\n",
       "       920, 930, 940, 950, 960, 970, 980, 990])},\n",
       "                   verbose=True)"
      ]
     },
     "execution_count": 74,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rs_rf=RandomizedSearchCV(RandomForestClassifier(),\n",
    "                        param_distributions=rf_grid,\n",
    "                        cv=5,\n",
    "                        n_iter=20,\n",
    "                        verbose=True)\n",
    "\n",
    "rs_rf.fit(X,y)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 75,
   "id": "52705ce8",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0.8000000000000002"
      ]
     },
     "execution_count": 75,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rs_rf.best_score_"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 76,
   "id": "b26678dc",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "{'n_estimators': 960,\n",
       " 'min_samples_split': 2,\n",
       " 'min_samples_leaf': 10,\n",
       " 'max_features': 'sqrt',\n",
       " 'max_depth': 3}"
      ]
     },
     "execution_count": 76,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rs_rf.best_params_"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 77,
   "id": "f18e3cc6",
   "metadata": {},
   "outputs": [],
   "source": [
    "# LogisticRegression score Before Hyperparameter Tuning: 80.48"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 78,
   "id": "9e2b666f",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<style>#sk-container-id-4 {color: black;}#sk-container-id-4 pre{padding: 0;}#sk-container-id-4 div.sk-toggleable {background-color: white;}#sk-container-id-4 label.sk-toggleable__label {cursor: pointer;display: block;width: 100%;margin-bottom: 0;padding: 0.3em;box-sizing: border-box;text-align: center;}#sk-container-id-4 label.sk-toggleable__label-arrow:before {content: \"▸\";float: left;margin-right: 0.25em;color: #696969;}#sk-container-id-4 label.sk-toggleable__label-arrow:hover:before {color: black;}#sk-container-id-4 div.sk-estimator:hover label.sk-toggleable__label-arrow:before {color: black;}#sk-container-id-4 div.sk-toggleable__content {max-height: 0;max-width: 0;overflow: hidden;text-align: left;background-color: #f0f8ff;}#sk-container-id-4 div.sk-toggleable__content pre {margin: 0.2em;color: black;border-radius: 0.25em;background-color: #f0f8ff;}#sk-container-id-4 input.sk-toggleable__control:checked~div.sk-toggleable__content {max-height: 200px;max-width: 100%;overflow: auto;}#sk-container-id-4 input.sk-toggleable__control:checked~label.sk-toggleable__label-arrow:before {content: \"▾\";}#sk-container-id-4 div.sk-estimator input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-4 div.sk-label input.sk-toggleable__control:checked~label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-4 input.sk-hidden--visually {border: 0;clip: rect(1px 1px 1px 1px);clip: rect(1px, 1px, 1px, 1px);height: 1px;margin: -1px;overflow: hidden;padding: 0;position: absolute;width: 1px;}#sk-container-id-4 div.sk-estimator {font-family: monospace;background-color: #f0f8ff;border: 1px dotted black;border-radius: 0.25em;box-sizing: border-box;margin-bottom: 0.5em;}#sk-container-id-4 div.sk-estimator:hover {background-color: #d4ebff;}#sk-container-id-4 div.sk-parallel-item::after {content: \"\";width: 100%;border-bottom: 1px solid gray;flex-grow: 1;}#sk-container-id-4 div.sk-label:hover label.sk-toggleable__label {background-color: #d4ebff;}#sk-container-id-4 div.sk-serial::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: 0;}#sk-container-id-4 div.sk-serial {display: flex;flex-direction: column;align-items: center;background-color: white;padding-right: 0.2em;padding-left: 0.2em;position: relative;}#sk-container-id-4 div.sk-item {position: relative;z-index: 1;}#sk-container-id-4 div.sk-parallel {display: flex;align-items: stretch;justify-content: center;background-color: white;position: relative;}#sk-container-id-4 div.sk-item::before, #sk-container-id-4 div.sk-parallel-item::before {content: \"\";position: absolute;border-left: 1px solid gray;box-sizing: border-box;top: 0;bottom: 0;left: 50%;z-index: -1;}#sk-container-id-4 div.sk-parallel-item {display: flex;flex-direction: column;z-index: 1;position: relative;background-color: white;}#sk-container-id-4 div.sk-parallel-item:first-child::after {align-self: flex-end;width: 50%;}#sk-container-id-4 div.sk-parallel-item:last-child::after {align-self: flex-start;width: 50%;}#sk-container-id-4 div.sk-parallel-item:only-child::after {width: 0;}#sk-container-id-4 div.sk-dashed-wrapped {border: 1px dashed gray;margin: 0 0.4em 0.5em 0.4em;box-sizing: border-box;padding-bottom: 0.4em;background-color: white;}#sk-container-id-4 div.sk-label label {font-family: monospace;font-weight: bold;display: inline-block;line-height: 1.2em;}#sk-container-id-4 div.sk-label-container {text-align: center;}#sk-container-id-4 div.sk-container {/* jupyter's `normalize.less` sets `[hidden] { display: none; }` but bootstrap.min.css set `[hidden] { display: none !important; }` so we also need the `!important` here to be able to override the default hidden behavior on the sphinx rendered scikit-learn.org. See: https://github.com/scikit-learn/scikit-learn/issues/21755 */display: inline-block !important;position: relative;}#sk-container-id-4 div.sk-text-repr-fallback {display: none;}</style><div id=\"sk-container-id-4\" class=\"sk-top-container\"><div class=\"sk-text-repr-fallback\"><pre>RandomForestClassifier(max_depth=5, min_samples_leaf=5, min_samples_split=5,\n",
       "                       n_estimators=270)</pre><b>In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook. <br />On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.</b></div><div class=\"sk-container\" hidden><div class=\"sk-item\"><div class=\"sk-estimator sk-toggleable\"><input class=\"sk-toggleable__control sk-hidden--visually\" id=\"sk-estimator-id-10\" type=\"checkbox\" checked><label for=\"sk-estimator-id-10\" class=\"sk-toggleable__label sk-toggleable__label-arrow\">RandomForestClassifier</label><div class=\"sk-toggleable__content\"><pre>RandomForestClassifier(max_depth=5, min_samples_leaf=5, min_samples_split=5,\n",
       "                       n_estimators=270)</pre></div></div></div></div></div>"
      ],
      "text/plain": [
       "RandomForestClassifier(max_depth=5, min_samples_leaf=5, min_samples_split=5,\n",
       "                       n_estimators=270)"
      ]
     },
     "execution_count": 78,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "## Save The Model\n",
    "\n",
    "X=data1.drop('Loan_Status', axis=1)\n",
    "y=data1['Loan_Status']\n",
    "\n",
    "rf=RandomForestClassifier(n_estimators=270,\n",
    "                         min_samples_split=5,\n",
    "                         min_samples_leaf=5,\n",
    "                         max_features='sqrt',\n",
    "                         max_depth=5)\n",
    "\n",
    "rf.fit(X,y)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 79,
   "id": "14fd84c3",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "['Loan_status_predict']"
      ]
     },
     "execution_count": 79,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "import joblib\n",
    "\n",
    "joblib.dump(rf, 'Loan_status_predict')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 80,
   "id": "5ffa6b6e",
   "metadata": {},
   "outputs": [],
   "source": [
    "model=joblib.load('loan_status_predict')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 81,
   "id": "eb9633e2",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Gender</th>\n",
       "      <th>Married</th>\n",
       "      <th>Education</th>\n",
       "      <th>Self_Employed</th>\n",
       "      <th>Dependents</th>\n",
       "      <th>ApplicantIncome</th>\n",
       "      <th>CoapplicantIncome</th>\n",
       "      <th>LoanAmount</th>\n",
       "      <th>Loan_Amount_Term</th>\n",
       "      <th>Credit_History</th>\n",
       "      <th>Property_Area</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>1</td>\n",
       "      <td>1</td>\n",
       "      <td>0</td>\n",
       "      <td>0</td>\n",
       "      <td>2</td>\n",
       "      <td>2889</td>\n",
       "      <td>0.0</td>\n",
       "      <td>45</td>\n",
       "      <td>180</td>\n",
       "      <td>0</td>\n",
       "      <td>1</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Gender  Married  Education  Self_Employed  Dependents  ApplicantIncome  \\\n",
       "0       1        1          0              0           2             2889   \n",
       "\n",
       "   CoapplicantIncome  LoanAmount  Loan_Amount_Term  Credit_History  \\\n",
       "0                0.0          45               180               0   \n",
       "\n",
       "   Property_Area  \n",
       "0              1  "
      ]
     },
     "execution_count": 81,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "import pandas as pd\n",
    "df=pd.DataFrame({\n",
    "    'Gender':1,\n",
    "    'Married':1,\n",
    "    'Education':0,\n",
    "    'Self_Employed':0,\n",
    "    'Dependents':2,\n",
    "    'ApplicantIncome':2889,\n",
    "    'CoapplicantIncome':0.0,\n",
    "    'LoanAmount':45,\n",
    "    'Loan_Amount_Term':180,\n",
    "    'Credit_History':0,\n",
    "    'Property_Area':1\n",
    "}, index=[0])\n",
    "\n",
    "df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 82,
   "id": "b6b9eb54",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Loan Not Approved\n"
     ]
    }
   ],
   "source": [
    "result=model.predict(df)\n",
    "\n",
    "if result==1:\n",
    "    print(\"Loan Approved\")\n",
    "else:\n",
    "    print(\"Loan Not Approved\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 95,
   "id": "4389cdbe",
   "metadata": {},
   "outputs": [],
   "source": [
    "# ------------------------------------------------------------------------\n",
    "## GUI\n",
    "\n",
    "from tkinter import *\n",
    "import joblib\n",
    "import pandas as pd"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 96,
   "id": "25095527",
   "metadata": {},
   "outputs": [],
   "source": [
    "def show_entry():\n",
    "    p1=float(e1.get())\n",
    "    p2=float(e2.get())\n",
    "    p3=float(e3.get())\n",
    "    p4=float(e4.get())\n",
    "    p5=float(e5.get())\n",
    "    p6=float(e6.get())\n",
    "    p7=float(e7.get())\n",
    "    p8=float(e8.get())\n",
    "    p9=float(e9.get())\n",
    "    p10=float(e10.get())\n",
    "    p11=float(e11.get())\n",
    "    \n",
    "    model=joblib.load('loan_status_predict')\n",
    "    df=pd.DataFrame({\n",
    "        'Gender':p1,\n",
    "        'Married':p2,\n",
    "        'Education':p3,\n",
    "        'Self_Employed':p4,\n",
    "        'Dependents':p5,\n",
    "        'ApplicantIncome':p6,\n",
    "        'CoapplicantIncome':p7,\n",
    "        'LoanAmount':p8,\n",
    "        'Loan_Amount_Term':p9,\n",
    "        'Credit_History':p10,\n",
    "        'Property_Area':p11\n",
    "    }, index=[0])\n",
    "    result=model.predict(df)\n",
    "    \n",
    "    if result==1:\n",
    "        Label(master, text=\"Loan Approved\").grid(row=31)\n",
    "    else:\n",
    "        Label(master, text=\"Loan Not Approved\").grid(row=31)\n",
    "        \n",
    "master=Tk()\n",
    "master.title(\"Loan Status Prediction Using Machine Learning\")\n",
    "label=Label(master, text=\"Loan Status Prediction\", bg=\"black\", fg=\"white\").grid(row=0, columnspan=2)\n",
    "\n",
    "Label(master, text=\"Gender [1:Male, 0:Female]\").grid(row=1)\n",
    "Label(master, text=\"Married [1:Yes, 0:No]\").grid(row=2)\n",
    "Label(master, text=\"Education\").grid(row=3)\n",
    "Label(master, text=\"Self_Employed\").grid(row=4)\n",
    "Label(master, text=\"Dependents [1,2,3,4]\").grid(row=5)\n",
    "Label(master, text=\"ApplicantIncome\").grid(row=6)\n",
    "Label(master, text=\"CoapplicantIncome\").grid(row=7)\n",
    "Label(master, text=\"LoanAmount\").grid(row=8)\n",
    "Label(master, text=\"Loan_Amount_Term\").grid(row=9)\n",
    "Label(master, text=\"Credit_History\").grid(row=10)\n",
    "Label(master, text=\"Property_Area\").grid(row=11)\n",
    "\n",
    "e1=Entry(master)\n",
    "e2=Entry(master)\n",
    "e3=Entry(master)\n",
    "e4=Entry(master)\n",
    "e5=Entry(master)\n",
    "e6=Entry(master)\n",
    "e7=Entry(master)\n",
    "e8=Entry(master)\n",
    "e9=Entry(master)\n",
    "e10=Entry(master)\n",
    "e11=Entry(master)\n",
    "\n",
    "e1.grid(row=1, column=1)\n",
    "e2.grid(row=2, column=1)\n",
    "e3.grid(row=3, column=1)\n",
    "e4.grid(row=4, column=1)\n",
    "e5.grid(row=5, column=1)\n",
    "e6.grid(row=6, column=1)\n",
    "e7.grid(row=7, column=1)\n",
    "e8.grid(row=8, column=1)\n",
    "e9.grid(row=9, column=1)\n",
    "e10.grid(row=10, column=1)\n",
    "e11.grid(row=11, column=1)\n",
    "\n",
    "Button(master, text=\"Predict\", command=show_entry).grid()\n",
    "\n",
    "mainloop()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "374f0ae0",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.11.4"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}

