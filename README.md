FITBIT HEALTH TECH ANALYTICS PROJECT REPORT

	Problem Statement

Modern wearable architecture relies on accurate calorie tracking to drive user engagement. While sensors directly monitor real-time heart rates, contextual markers—such as hydration profiles, session lengths, and user background—introduce complex non-linear dynamics into total energy burn. 

This project solves these issues via a two-fold engineering system:

	**Supervised Analytics**: Creates a robust, production-ready continuous regression estimator to map metabolic outputs accurately.

	**Unsupervised Discovery**: Reduces high-dimensional sensor spaces to expose overlapping behavioural fitness cohorts without categorical tracking labels.

	Exploratory Data Analysis (EDA) Findings


•	**Target Behavior**: Calorie burn showcases a normal distribution tail with rightward skewing on heavy high-intensity workouts.

•	**Feature Covariance**: High physiological multi-collinearity exists between `Avg_BPM` and `Max_BPM`. Robust regularization is required to handle these dependencies.


•	**Sensor Variance**: Missing values discovered across physiological tracking dimensions (e.g., body mass variations) indicate missing device connections. These are handled via safe median imputations to preserve sample volume.

	Supervised Model Comparison Matrix

•	The structured pipeline yielded the following experimental performance data:

•	| Machine Learning Model | MAE  | RMSE |) | R2 Score Deployment Recommendation |

•	| **XGBoost Regressor** | ** 4.34  | **7.00  ** | ** 0.9984 ** |**Optimal Cloud Endpoint** |
•	| **Random Forest** | 3.80 | 7.69 | 0.9981| Robust Ensembling |

•	| **Decision Tree** | 8.27 | 13.95 | 0.9938 |Prone to Overfitting |

•	| ** Support Vector Regression ** | 12.24 | 29.01| 0.9732| **Optimal Mobile On-Device** |

•	| **Linear Regression** | 34.62 | 52.77| 0.9113| Sensitive to Multicollinearity |

	Key Selection Insights:

•	**The Acceptance Threshold (\(\ge 0.80\))** is successfully cleared by all candidates.

•	**XGBoost** achieves the highest accuracy (\(R^2 = 0.9984 \)). It is best suited for deployment as an API endpoint inside cloud environments where maximum precision is needed.


•	** Linear Regression ** delivers acceptable accuracy (\(R^2 = 0.9113\)) with zero execution overhead. This makes it ideal for direct embedded compilation into smartwatch hardware or client-side mobile applications to protect battery life.

	Unsupervised Clustering & PCA Discoveries

•	**Structural Separability**: The system achieved a **Silhouette Score of 0.2450**. This surpasses the acceptance target of \(\ge 0.15\), confirming distinct behavioral profiles despite the standard overlapping nature of human fitness metrics.

•	**Variance Recovery**: Compressing features down to two primary principal components captures over **70% of total contextual variance**, ensuring a clear and informative visualization space.

	Profile Matrix Interpretation:

•	**Cluster 0 (The Casual Starters) **: Features short workout lengths (under 35 minutes) alongside moderate heart rates. Users match beginner demographics. **In-App Action**: Recommend basic hydration goals and consistency milestones.

•	**Cluster 1 (The High-Intensity Group) **: Characterized by elevated heart rates (\(\ge 150\) BPM) paired with high body-fat percentages. **In-App Action**: Monitor cardiovascular limits and suggest structured recovery pacing window rules.

•	**Cluster 2 (The Endurance Veterans) **: Features long training windows (\(\ge 85\) minutes) and low resting heart rates. **In-App Action**: Prompt premium tools for advanced performance tracking and long-term nutrition planning.

	Strategic Business Insights

•	**Optimize Sensor Procurement**: Feature importance plots show that heart rate dynamics and session lengths capture over 80% of calorie-burn variance. Device teams can safely transition away from complex user-facing entry menus (like manual water or food logging) without sacrificing estimation accuracy.

•	**Dynamic UI Adaptation**: The system can track user metrics across a trailing 7-day window to dynamically reassign their cluster segment. The mobile application can then automatically customize UI elements, promoting endurance challenges to veteran clusters and low-impact activity programs to casual clusters.





