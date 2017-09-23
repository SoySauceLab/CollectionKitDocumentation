# CollectionKit

A modern Swift framework for building reusable data-driven collection components.

[![Carthage compatible](https://img.shields.io/badge/Carthage-Compatible-brightgreen.svg?style=flat)](https://github.com/Carthage/Carthage)
[![Version](https://img.shields.io/cocoapods/v/CollectionKit.svg?style=flat)](http://cocoapods.org/pods/CollectionKit)
[![License](https://img.shields.io/cocoapods/l/CollectionKit.svg?style=flat)](https://github.com/SoySauceLab/CollectionKit/blob/master/LICENSE?raw=true)
[![Build Status](https://travis-ci.org/SoySauceLab/CollectionKit.svg?branch=master)](https://travis-ci.org/SoySauceLab/CollectionKit)
[![codecov](https://codecov.io/gh/SoySauceLab/CollectionKit/branch/master/graph/badge.svg)](https://codecov.io/gh/SoySauceLab/CollectionKit)
![Xcode 8.2+](https://img.shields.io/badge/Xcode-8.2%2B-blue.svg)
![iOS 8.0+](https://img.shields.io/badge/iOS-8.0%2B-blue.svg)
![Swift 3.0+](https://img.shields.io/badge/Swift-3.0%2B-orange.svg)

### Features

* Declaritive API for building collection view components
* Automatically update UI when data changes
* Composable & hot swappable sections, layouts, & animations
* Strong type checking powered by Swift Generics
* Reuse everything!

We think that populating collection view content should be as simple as building custom UIViews. Sections should be reusable and composable into one another. They should define their own layout be easily animatable as well. CollectionKit is our attempt in solving these problems. UICollectionView has been around for 10 years. It is time that we come up with something better **with Swift**.

Unlike traditional UICollectionView's `datasource`/`delegate` methods, CollectionKit uses a single **Provider** object that tells `CollectionView` exactly how to display & handle a collection.

These Providers are easy to construct, and infinitely composable. Providers also have their own animation and layout objects. You can have sections that layouts and behave differently with in a single `CollectionView`.

CollectionKit already provides many of the commonly used Providers out of the box. But you can still easily create reuseable Provider classes that generalizes on different types on data. Checkout examples down below!

## Install

via **CocoaPods** or **Carthage**.

## Usage

Getting started at [Build your first provider](basic-example.md).
