<p align="center">
  <a href="https://fidesinnova.io/" target="blank"><img src="g-c-web-back.png" /></a>
</p>

# Introduction 

<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
<a href="https://circleci.com/gh/nestjs/nest" target="_blank"><img src="https://img.shields.io/circleci/build/github/nestjs/nest/master" alt="CircleCI" /></a>
<a href="https://coveralls.io/github/nestjs/nest?branch=master" target="_blank"><img src="https://coveralls.io/repos/github/nestjs/nest/badge.svg?branch=master#9" alt="Coverage" /></a>
<a href="https://discord.com/invite/NQdM6JGwcs" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
<a href="https://twitter.com/Fidesinnova" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow"></a>

#### Revolutionizing Decentralized IoT Systems
Fides Innova is dedicated to transforming the landscape of decentralized and reliable IoT systems. Our platform, underpinned by cutting-edge blockchain technology, focuses on zk-IoT devices to ensure seamless, secure communication, and a network founded on trust and transparency.
<figure><img src=".gitbook/assets/Intro.jpg" alt=""><figcaption></figcaption></figure>

#### Key Features

* **FidesInnova Blockchain Node**: Our robust blockchain node, equipped with ZKP-enabled JavaScript execution, ensures the secure and authentic execution of Service Contracts, providing a solid foundation for our ecosystem.
* **FidesInnova IoT Node**: Designed for efficiency and reliability, the IoT Node integrates seamlessly with our blockchain technology, enhancing the functionality and security of IoT devices across the network.
* **FidesInnova Web App**: This intuitive web application allows users to create, manage, and monetize Service Contracts effortlessly. It serves as a powerful tool for extending the capabilities of IoT devices and managing your decentralized services.
* **FidesInnova Mobile App**: Available on major app stores, our mobile app offers users unparalleled control over their IoT devices, bringing convenience and functionality to your fingertips.

#### Empowering Users and Expanding Possibilities

FidesInnova is more than just a platform; it's a holistic ecosystem that empowers users through its suite of applications and services. Explore our ecosystem, engage with our technologies, and experience a new standard in decentralized IoT solutions.

Join us on this journey towards a more transparent, secure, and innovative future.


# Table of contents

* [Introduction](README.md)
* [Tech Stack](tech-stack/README.md)
  * [Service Contract](tech-stack/service-contract.md)
  * [ZKP-enabled JavaScript Execution](tech-stack/zkp-enabled-javascript-execution.md)
  * [Service Market](tech-stack/service-market.md)
  * [Message Queuing Telemetry Transport (MQTT) protocol](tech-stack/message-queuing-telemetry-transport-mqtt-protocol.md)
* [Connecting Your MetaMask to the Network](connecting-your-metamask-to-the-network.md)
* [Browsing the Fides Innova ZKP Network](browsing-the-fides-innova-zkp-network.md)
* [Mobile App](mobile-app.md)
* [Web App (User Panel, Admin Panel)](web-app-user-panel-admin-panel.md)
* [Full Node](full-node.md)
* [Publishing Service Contracts on the Fides Innova Blockchain](publishing-service-contracts-on-the-fides-innova-blockchain.md)
* [Fides Zero-Knowledge Proof (ZKP) Algorithm](fides-zero-knowledge-proof-zkp-algorithm/README.md)
  * [1- Setup Phase](fides-zero-knowledge-proof-zkp-algorithm/1-setup-phase/README.md)
    * [Example 1](fides-zero-knowledge-proof-zkp-algorithm/1-setup-phase/example-1.md)
    * [Example 2](fides-zero-knowledge-proof-zkp-algorithm/1-setup-phase/example-2.md)
  * [2- Commitment Phase](fides-zero-knowledge-proof-zkp-algorithm/2-commitment-phase/README.md)
    * [Target architecture - RISC-V RV32IM](fides-zero-knowledge-proof-zkp-algorithm/2-commitment-phase/target-architecture-risc-v-rv32im.md)
    * [Target architecture - Cortex-A53 - for Siemens SIMATIC IOT2050](fides-zero-knowledge-proof-zkp-algorithm/2-commitment-phase/target-architecture-cortex-a53-for-siemens-simatic-iot2050.md)
    * [Example 1](fides-zero-knowledge-proof-zkp-algorithm/2-commitment-phase/example-1.md)
    * [Example 2](fides-zero-knowledge-proof-zkp-algorithm/2-commitment-phase/example-2.md)
  * [3- Proof Generation Phase](fides-zero-knowledge-proof-zkp-algorithm/3-proof-generation-phase/README.md)
    * [Example 1](fides-zero-knowledge-proof-zkp-algorithm/3-proof-generation-phase/example-1/README.md)
      * [Target architecture - ARMv6-M Cortex-M0 32-bit ARM - RaspberryPi Pico](fides-zero-knowledge-proof-zkp-algorithm/3-proof-generation-phase/example-1/target-architecture-armv6-m-cortex-m0-32-bit-arm-raspberrypi-pico.md)
    * [Example 2](fides-zero-knowledge-proof-zkp-algorithm/3-proof-generation-phase/example-2.md)
  * [4- Proof Verification Phase](fides-zero-knowledge-proof-zkp-algorithm/4-proof-verification-phase/README.md)
    * [Example 1](fides-zero-knowledge-proof-zkp-algorithm/4-proof-verification-phase/example-1.md)
    * [Example 2](fides-zero-knowledge-proof-zkp-algorithm/4-proof-verification-phase/example-2.md)
* [ZKP and IoT Device Firmware Integration (zk-Device Design)](zkp-and-iot-device-firmware-integration-zk-device-design/README.md)
  * [E-Card; a sample zk-Device](zkp-and-iot-device-firmware-integration-zk-device-design/e-card-a-sample-zk-device/README.md)
    * [Instruction Set Architecture (ISA)](zkp-and-iot-device-firmware-integration-zk-device-design/e-card-a-sample-zk-device/instruction-set-architecture-isa.md)
    * [Installation](zkp-and-iot-device-firmware-integration-zk-device-design/e-card-a-sample-zk-device/installation.md)
    * [Reset](zkp-and-iot-device-firmware-integration-zk-device-design/e-card-a-sample-zk-device/reset.md)
    * [Mesh IoT Network](zkp-and-iot-device-firmware-integration-zk-device-design/e-card-a-sample-zk-device/mesh-iot-network.md)

