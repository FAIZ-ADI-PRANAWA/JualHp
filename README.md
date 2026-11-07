# JualHp 📱

This project is an Android application developed in Kotlin that showcases a mobile phone e-commerce experience. It allows users to browse a list of mobile phones, view their details, and fetch product information from an external API. The application is built using Jetpack Compose for the UI and Retrofit for network operations.

## Badges 🏆

| Badge | Description |
|---|---|
| ![Kotlin](https://img.shields.io/badge/kotlin-1B5F83?style=for-the-badge&logo=kotlin&logoColor=white) | Developed with Kotlin |
| ![Jetpack Compose](https://img.shields.io/badge/Jetpack_Compose-4285F4?style=for-the-badge&logo=jetpack-compose&logoColor=white) | UI implemented with Jetpack Compose |
| ![Retrofit](https://img.shields.io/badge/Retrofit-00A9E0?style=for-the-badge&logo=retrofit&logoColor=white) | Network requests handled by Retrofit |

## Table of Contents 📜

- [Project Title & Badges](#jualhp-📱)
- [Description](#description-ℹ️)
- [Table of Contents](#table-of-contents-📜)
- [Features](#features-✨)
- [Tech Stack](#tech-stack-💻)
- [Installation](#installation-🚀)
- [Usage](#usage-💡)
- [Project Structure](#project-structure-📁)
- [API Reference](#api-reference-🌐)
- [Contributing](#contributing-🤝)
- [License](#license-⚖️)
- [Footer](#footer-❤️)

## Description ℹ️

The JualHp application is a simple yet functional e-commerce app designed to display mobile phone products. It fetches product data from the `https://dummyjson.com/` API and presents it to the user in a clear and intuitive interface. The app demonstrates fundamental Android development concepts, including navigation, network requests, and modern UI development with Jetpack Compose.

## Features ✨

- **Product Listing:** Display a list of mobile phones with their essential details (title, price, rating). 📱
- **Product Details:** View detailed information for each product, including description and image. 🖼️
- **API Integration:** Fetches product data from a remote API using Retrofit. 🌐
- **Jetpack Compose UI:** Built with modern Android UI toolkit for a declarative and efficient UI. ✨
- **Navigation:** Smooth navigation between the product list and product detail screens using Jetpack Navigation Component. ➡️
- **Testing:** Includes basic unit and instrumented tests. 🧪

## Tech Stack 💻

- **Language:** Kotlin
- **UI Toolkit:** Jetpack Compose
- **Networking:** Retrofit, Gson
- **Architecture:** MVVM (Model-View-ViewModel)
- **Testing:** JUnit, AndroidX Test

## Installation 🚀

To build and run this project, you need to have Android Studio installed and configured.

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/FAIZ-ADI-PRANAWA/JualHp.git
    cd JualHp
    ```

2.  **Open the project in Android Studio:**
    -   Go to `File > Open...` and select the `JualHp` directory.

3.  **Sync Gradle:**
    -   Android Studio will automatically prompt you to sync your project with Gradle files. If not, go to `File > Sync Project with Gradle Files`.

4.  **Run the application:**
    -   Connect an Android device or start an emulator.
    -   Click the `Run` button (green triangle) in Android Studio. Select your device/emulator and the app will be built and installed.

**Dependencies:**
This project relies on external libraries managed by Gradle. The specific versions are defined in `gradle/libs.versions.toml`. Ensure a stable internet connection during the Gradle sync to download these dependencies.

## Usage 💡

The JualHp application is designed to provide a seamless product browsing experience.

1.  **Launch the App:** Upon launching, you will see a list of mobile phones.
2.  **Browse Products:** Scroll through the list to view different phone models. Each item displays the product title, price, and rating.
3.  **View Details:** Tap on any product in the list to navigate to its detailed view. Here, you can see the product's image, full description, and price.
4.  **Navigate Back:** Use the back arrow in the top-left corner of the details screen to return to the product list.

**Example Scenario:**
Imagine a user looking for a new smartphone. They open the JualHp app, scroll through the available options, and find an interesting model. They tap on it to see more details, zoom in on the image, read the description, and check the price. If satisfied, they might consider purchasing it (though purchasing functionality is not implemented in this version).

```kotlin
// Example of fetching product list in the ViewModel:
// Inside ProductListViewModel.kt
private fun fetchProducts() {
    viewModelScope.launch {
        try {
            _products.value = repository.getProducts()
        } catch (e: Exception) {
            e.printStackTrace()
        }
    }
}
```

```kotlin
// Example of navigating to product details:
// Inside MainActivity.kt's AppNavigation function
composable("productList") {
    ProductListScreen(viewModel) { productId ->
        navController.navigate("productDetails/orEach productId")
    }
}
```

## Project Structure 📁

The project follows a standard Android project structure with an MVVM architecture:

```
JualHp/
├── app/
│   ├── build.gradle.kts
│   ├── proguard-rules.pro
│   ├── src/
│   │   ├── androidTest/
│   │   │   └── java/com/example/jualhp/ExampleInstrumentedTest.kt
│   │   ├── main/
│   │   │   ├── AndroidManifest.xml
│   │   │   ├── java/com/example/jualhp/
│   │   │   │   ├── MainActivity.kt
│   │   │   │   ├── data/
│   │   │   │   │   ├── model/Product.kt
│   │   │   │   │   ├── repository/ProductRepository.kt
│   │   │   │   │   └── service/
│   │   │   │   │       ├── ApiClient.kt
│   │   │   │   │       └── ApiService.kt
│   │   │   │   └── ui/
│   │   │   │       ├── details/
│   │   │   │       │   ├── ProductDetailsScreen.kt
│   │   │   │       │   └── ProductDetailsViewModel.kt
│   │   │   │       └── productlist/
│   │   │   │           ├── ProductListScreen.kt
│   │   │   │           └── ProductListViewModel.kt
│   │   │   └── res/
│   │   │       ├── drawable/
│   │   │       ├── mipmap-hdpi/
│   │   │       ├── ... (other mipmap folders)
│   │   │       ├── values/
│   │   │       └── xml/
│   │   └── test/
│   │       └── java/com/example/jualhp/ExampleUnitTest.kt
├── gradle/
│   ├── wrapper/
│   │   ├── gradle-wrapper.jar
│   │   └── gradle-wrapper.properties
├── .idea/
├── build.gradle.kts
├── gradle.properties
├── gradlew
├── gradlew.bat
└── settings.gradle.kts
```

-   **`app/src/main/java/com/example/jualhp`**: Contains the main application code, including:
    -   `MainActivity.kt`: The entry point of the application.
    -   `data`: Models, repositories, and API services for data handling.
    -   `ui`: Composable screens and ViewModels for the user interface.
-   **`app/src/main/res`**: Contains application resources like layouts, drawables, and values.
-   **`app/src/androidTest` & `app/src/test`**: Contains instrumented and unit tests, respectively.

## API Reference 🌐

The application interacts with the DummyJSON API to fetch product data.

-   **Base URL:** `https://dummyjson.com/`
-   **Endpoint for Products:**
    -   `GET /c/2483-f5be-4a82-8b30`
    -   This endpoint returns a `CategoryProductResponse` which contains a list of `Product` objects.

**Data Models:**

*   `CategoryProductResponse`:
    ```kotlin
data class CategoryProductResponse(
    val categoryId: String,
    val categoryName: String,
    val products: List<Product>
)
    ```
*   `Product`:
    ```kotlin
data class Product(
    val id: Int,
    val title: String,
    val description: String,
    val price: Int,
    val rating: Float,
    val image: String
)
    ```

## Contributing 🤝

Contributions are welcome! If you have any suggestions or improvements, please feel free to:

1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/your-feature-name`).
3.  Make your changes.
4.  Commit your changes (`git commit -m 'Add some feature'`).
5.  Push to the branch (`git push origin feature/your-feature-name`).
6.  Open a Pull Request.

Please ensure your code adheres to the existing style and includes relevant tests.

## License ⚖️

This project does not explicitly specify a license. Please refer to the repository owner for licensing details.

## Footer ❤️

**JualHp**

🔗 [Repository URL](https://github.com/FAIZ-ADI-PRANAWA/JualHp)

Created by [FAIZ ADI PRANAWA](https://github.com/FAIZ-ADI-PRANAWA)

--- 

[![Star](https://img.shields.io/github/stars/FAIZ-ADI-PRANAWA/JualHp?style=social)](https://github.com/FAIZ-ADI-PRANAWA/JualHp/stargazers)
[![Fork](https://img.shields.io/github/forks/FAIZ-ADI-PRANAWA/JualHp?style=social)](https://github.com/FAIZ-ADI-PRANAWA/JualHp/fork)
[![GitHub issues](https://img.shields.io/github/issues/FAIZ-ADI-PRANAWA/JualHp)](https://github.com/FAIZ-ADI-PRANAWA/JualHp/issues)

Give a ⭐️ if you like this project!


---
**<p align="center">Generated by [ReadmeCodeGen](https://www.readmecodegen.com/)</p>**