---
layout: post
title:  "Analog-Digital Converter"
date:   2023-10-04 19:31:29 +0900
categories: Design
order: 4
---

Low oversampling에서는 ADC가 circuit imperfection에 엄청 민감해진다.
32~256정도를 쓰고, 4,8정도가 low oversampling이다.

ADC에서 사용하는 clock이 더 낮아야 interrupt가 덜 걸린다?
interrupt가 뭐지
interrupt map은 또 뭐지


The choice of ADC architecture depends heavily on the application's requirements, particularly concerning speed, resolution, and power efficiency. Flash ADCs offer unmatched speed but at the cost of high complexity and power consumption, while SAR ADCs are ideal for moderate-speed, high-resolution, and power-sensitive designs. Pipelined ADCs strike a balance between speed and resolution, while noise-shaping SAR ADCs improve noise performance in precision systems. Finally, Delta-Sigma ADCs shine in applications requiring the highest resolution and noise immunity but are limited in speed.

Hard-working LNADC:
지금까지는 ADC 앞단에 많은 amplifier들이 쓰였고, 이 amplifier들이 power를 엄청나게 먹었다.
정작 ADC는 power를 거의 안먹었다.

여기서 amplifier를 안쓰면? 신호가 작으니 SNR이 아주 안좋게 들어올 것이다.
이때는 ADC가 먹는 power를 올려서 SNR을 개선해야 한다.

이러면 또 power가 그게 그거일 수도 있지만, 어쨌든 Amplifier 빼고 ADC만 쓰자는 이야기다.



Flash ADC:


양자화 기준점마다 비교기를 두고 샘플된 인풋에 대해 모든 비교기가 동시에 동작하는 방식의 ADC. 속도가 매우 빠르다는 장점이 있지만 N-bit 변환을 위해 2^N - 1개의 비교기가 필요하므로 고해상도에는 적합하지 않고 전력 소모가 심하다. 보통 5bit 이하에 저해상도이면서 고속 동작을 요구하는 어플리케이션에 이용된다.
Flash ADCs, also known as parallel ADCs, are among the fastest ADC architectures, making them suitable for high-speed applications such as oscilloscopes and radar systems. A flash ADC consists of a large number of comparators operating in parallel, each comparing the input voltage to a reference voltage. For an n-bit ADC, 2^n−1 comparators are needed, along with a resistive ladder network to generate the reference voltages. Once the input signal is compared to the reference, the comparators generate a corresponding digital code in a single clock cycle.

Advantages:
Extremely fast conversion speed, often in the GHz range.

Disadvantages:
High power consumption due to the large number of comparators.
Exponential increase in hardware complexity as resolution increases.

Applications:
High-speed data acquisition systems, digital oscilloscopes, and radar signal processing.


SAR ADC
하나의 비교기와 Capacitor [3]-DAC을 이용한 ADC. 샘플된 인풋을 1개의 비교기가 양자화하고, 그 값에 따라 Capacitor-DAC을 스위칭해서 양자화 기준점을 바꾼다. 바뀐 기준점에 대해 비교기는 재귀적으로 동작한다. 따라서 기본적으로 N-bit 변환을 위해 비교기가 N번 동작하는 방식이다. Capacitor-DAC을 스위칭하는 디지털 로직 속도에 변환 속도가 많은 영향을 받기 때문에 공정이 진화해오면서 많은 수혜를 받은 구조이다. Flash보다는 이론적으로 느리지만 단 한개의 비교기만을 이용하기 때문에 전력소모가 매우 적고 고해상도로도 구현 가능하다. 게다가 면적도 적고 비교기 간의 미스매치를 보정해줄 필요도 없어 여러모로 장점이 많다. 어플리케이션에 맞게 속도와 해상도를 조절하기도 좋기 때문에, 폭넓은 분야에 사용된다.
SAR ADCs are widely used due to their balanced trade-off between speed, resolution, and power efficiency. SAR ADCs work by employing a binary search algorithm. The input signal is compared to a DAC-generated reference voltage at each step, and the most significant bit (MSB) is set or cleared based on whether the input is higher or lower than the reference. This process continues for each bit, achieving a complete conversion in n clock cycles for an n-bit ADC.

Advantages:
Low power consumption and moderate speed.
Suitable for medium- to high-resolution applications (typically 8 to 18 bits).

Disadvantages:
Conversion speed is slower compared to Flash ADCs.

Applications:
Sensor interfacing, battery-powered devices, and moderate-speed data acquisition systems.



Pipelined ADC
ADC를 내부적으로 두 개 이상의 스테이지를 구성해서 동작하는 방식. 스테이지간엔 보통 OP-amp와 capacitor를 이용해 이전 스테이지의 전압 정보를 증폭시켜 다음 스테이지로 전달한다. 고속이면서 고해상도를 가지기 위해서 필수적인 구조이다. 최근에는 공정 기술의 발달로 SAR의 속도는 비약적으로 향상된 데 반해, 정통적인 아날로그 회로인 OP-amp는 저전압 구조에도 적합하지 않은데다가 속도 향상도 크지 않아서 속도 향상에 병목이 걸려있다. 그래도 한 개의 스테이지로 구성된 ADC에는 한계가 있기 때문에 연구는 꾸준히 진행되고 있으며, 최근엔 OP-amp를 제거하고 Ring-amp나 Dynamic-Amp를 이용해서 Pipelined 구조를 구성하는 시도도 많이 이루어지고 있다. 또한 각 스테이지의 ADC를 SAR 방식으로 구성한 Pipelined SAR ADC 구조 역시 연구가 활발히 진행중이다.
Pipelined ADCs offer a compromise between speed and resolution, making them ideal for applications requiring medium-to-high speed with high resolution. The pipelined ADC architecture splits the conversion process into multiple stages. Each stage consists of a low-resolution ADC followed by a DAC. The output of each stage is amplified and passed on to the next stage, correcting errors progressively and refining the digital output. The pipeline architecture allows for concurrent processing of multiple samples, significantly increasing throughput.

Advantages:
High speed (faster than SAR ADCs but slower than Flash ADCs).
Efficient trade-off between speed and resolution, often used for 8 to 16 bits at multi-MSPS rates.

Disadvantages:
Increased complexity compared to SAR ADCs.
Requires careful calibration to correct for errors across stages.

Applications:
Imaging, video applications, and communication systems.



Noise-Shaping SAR ADC
SAR의 변환 이후 남은 잔여물을 인풋 쪽으로 피드백시켜서 에러의 양을 최소화 시키는 방식. DSM ADC와 SAR ADC의 장점을 합친 방식이라고 볼 수 있다. 해상도를 높이기 위해선 DSM과 마찬가지로 오버샘플링이 필수적인데, 최근엔 SAR ADC의 변환 속도가 꽤나 빨라지면서 중간 주파수대역에서 고해상도를 가지는 어플리케이션에 주로 이용되고 있다.
Noise-shaping SAR ADCs combine the benefits of SAR architecture with noise-shaping techniques to achieve higher effective resolution and better performance in noise-sensitive applications. In this hybrid approach, a conventional SAR ADC is used with oversampling and noise-shaping filters to push quantization noise to higher frequencies. This method improves the overall signal-to-noise ratio (SNR) without sacrificing speed or increasing power significantly.

Advantages:
Better noise performance than traditional SAR ADCs.
Efficient for achieving high resolutions while maintaining moderate power consumption.

Disadvantages:
More complex architecture due to noise-shaping circuitry.

Applications:
Audio processing, biomedical instrumentation, and precision measurement systems.



Single-slope (or dual-slope) ADC
비교기 인풋에 샘플된 인풋과 ramp 신호를 양자화기준점의 개수 만큼 비교하는 방식. 예를 들어 10bit를 구성하기 위해선 ramp 신호를 비교기 인풋에 인가하고 비교기를 1023번 동작시킨다. Flash ADC보다 나을 게 없어보이지만, 비교기를 한 개만 쓰기 때문에 많은 에러 소스로부터 자유롭다. 따라서 오히려 매우 고해상도를 목표로 하기 적합한 구조이지만, 대신 속도가 매우 느리다는 단점이 있다.




Delta sigma modulator (DSM) ADC
기존의 ADC는 모두 고정된 양자화 기준점을 가지고 한 번에 샘플된 인풋이 어느 기준점에 가장 가깝냐 판단하는 것으로 변환하였다. 즉 Flash든 SAR든 그 기준점을 어떻게 만드냐만 다를 뿐, 근본적으로 기준점에 갖다 대고 즉각적으로 비교한다는 것은 동일하다. 하지만 DSM은 기존의 ADC들은 한 번만 변환해서 알 값들을 추가적으로 샘플하는 오버샘플링 과정을 갖는다. 이는 샘플링 속도보다 인풋의 속도가 매우 느리다면, 필터링을 통해 양자화 에러를 원래의 고정된 값보다 줄일 수 있기 때문이다. 예를 들어 인풋이 고정된 값이라고 생각해보자. 인풋은 0.75로 꾸준히 유지되고, 양자화 기준점은 0.5 한개밖에 없다. (즉 1bit ADC이다.)
DSM은 이 0.75를 꾸준히 샘플하고, 비교기값에 따라 인풋에 feedback 한다. 이렇게 되면 비교기의 아웃풋은 111011101110..을 반복하게 된다.(전통적인 1차 DSM이라면) 여기서 1과 0의 개수를 평균낸다면(이는 저역통과 필터를 통과시킨다는 말과 같다.) 어떻게 될까? 평균값은 0.75가 된다. 즉 1bit ADC로도 정확한 input값을 예측할 수 있는 것이다. 이러한 방식의 ADC는 초창기엔 너무 많은 로직들이 필요하고, 속도 제한이 많아서 인정받지 못했지만 지금은 오디오 분야에서 초고해상도 변환을 위해선 필수적인 방법이다.

Delta-Sigma ADCs use oversampling and noise shaping to achieve very high resolution at relatively lower speeds. The architecture consists of a delta-sigma modulator, which oversamples the input signal and uses feedback to shape the noise spectrum. The high-frequency noise is filtered out, leaving a high-resolution digital representation of the input. ΔΣ ADCs typically require decimation filters to reduce the oversampled data to the desired rate.

Advantages:
Very high resolution (often 20 bits or more).
Superior noise performance, particularly for low-frequency signals.

Disadvantages:
Relatively slow conversion speed compared to other ADC types.
Requires complex digital filtering and processing stages.

Applications:
Precision measurement, audio applications (high-fidelity audio), and industrial control systems.




나무위키 ADC, DAC 문서 정리

Bosor - Wooley Delta Sigma ADC: Non-delayed integrator를 쓰는 ADC.
이 구조에서는 C가 줄어들면 input->output delay가 크게 감소한다.
그러면 신호가 한번에 훅 들어와서, quantizer 출력이 이상하게 나올 수 있다.

지금 문제는, C가 f corner일 때 ADC의 ENOB가 상당히 작게 나온다는 것이다.
결국, C가 작아지면 ENOB가 작게 나온다는 것이다.

앞에서 말한 문제가 맞는지 확인하기 위해, ADC에 집어넣는 전류를 줄여볼 수 있다.
전류를 줄이면 Amp BW가 줄어들어 Amp가 느려진다.
이때 출력이 정상적으로 나온다면, Amp가 너무 빨라서 생긴 settling time 문제였던 거다.


ADC 입력이 Quantizer로 바로 들어가게 하는 feed-forward 구조도 있고,
ADC 입력이 Integrator 2로 바로 들어가게 하는 feed-forward 구조도 있다.

Delta Sigma ADC에는 Single Stage Amp 쓰는게 가장 좋다. 2 stage부터는 전류만 많이 쓴다.


RF Amplifiers:
Gain을 늘리려면 Amp를 직렬로 여러개 연결해야 한다
출력 Power를 늘리려면 Amp를 병렬로 여러개 연결해야 한다




In digital systems, ADC clock speed plays a role in managing the rate of data conversions, affecting system interrupts and overall processing. Slower ADC clock speeds result in fewer interrupts because conversions occur less frequently, reducing the need for the processor to handle them. Interrupts are signals that alert the processor to execute specific routines when an event occurs, often triggered by hardware like ADCs. In IC design, an interrupt map refers to how interrupts are assigned to different system components, optimizing control and data flow for efficient performance.

Slower ADC Clock and Interrupts
When the clock speed of an ADC is slower, it means that the conversion process from analog to digital data takes more time. This reduced conversion rate directly impacts the number of interrupts generated by the system because each conversion typically triggers an interrupt to notify the processor that data is ready to be read.

Example:
High Clock Speed ADC: With fast conversion, an ADC operating at a higher frequency will produce more digital output values per second. This leads to more frequent interrupts, as each completed conversion triggers the system to process the new data.
Low Clock Speed ADC: A slower ADC clock reduces the rate at which conversions are completed, resulting in fewer interrupts. This can be beneficial when reducing processor load is crucial, especially in power-sensitive systems.
In summary, slower ADC clocks reduce the number of data conversions, hence generating fewer interrupts. This can be useful in applications where real-time data is not critical, or the system aims to reduce processor workload and power consumption.

Interrupts in IC Design
An interrupt is a signal sent to the processor by hardware or software that temporarily halts the current operations and shifts the processor's attention to handle an event (like data being ready from an ADC). Once the interrupt service routine (ISR) is executed to handle the event, the system resumes its prior operations.

Interrupts serve the purpose of:

Efficiently managing events in a non-blocking manner, allowing the CPU to execute other tasks until the event occurs.
Ensuring timely handling of high-priority tasks or inputs, such as reading sensor data, controlling motors, or responding to user inputs.
Key Types of Interrupts:

Hardware Interrupts: Triggered by external devices (e.g., ADCs, timers, sensors). For instance, after an ADC completes a conversion, it triggers an interrupt to notify the microcontroller to read the data.
Software Interrupts: Generated by software instructions, such as requesting a specific operation or handling an error.
Interrupt Map in IC Design
An interrupt map in IC design refers to the configuration and assignment of interrupt signals to specific processors or controller units in a system-on-chip (SoC) or microcontroller unit (MCU). It is essentially a table or structure that defines which hardware events are mapped to which interrupt lines or vectors.

Components of an Interrupt Map:
Interrupt Vector Table: This is a data structure that holds the addresses of interrupt service routines (ISR) for each interrupt request (IRQ). When an interrupt occurs, the CPU uses this table to find the correct ISR to handle the event.
Interrupt Priority Levels: In many ICs, interrupts are assigned different priority levels. Higher-priority interrupts can preempt lower-priority ones, ensuring that critical tasks are handled first.
Interrupt Controllers: These manage multiple interrupt sources and prioritize or aggregate them for the processor. They are used to prevent overload by controlling how and when the CPU responds to different interrupt sources.
For example, in a multi-core IC, different cores might be responsible for handling different types of interrupts based on their role in the system (e.g., core 1 handles sensor data, while core 2 manages network traffic). An efficient interrupt map optimizes the flow of data and minimizes latency by directing interrupts to the appropriate processing unit.

Conclusion
Slower ADC clock speeds reduce the number of interrupts, lessening the burden on the processor, which can be useful in power-sensitive systems or when real-time processing isn't critical. Interrupts themselves are mechanisms for handling asynchronous events efficiently, while an interrupt map in IC design optimizes how various interrupts are managed and assigned within the system. A well-designed interrupt map ensures system performance, stability, and responsiveness by prioritizing and organizing interrupt events.

Further Reading Suggestions:
Microcontroller interrupt handling and design patterns.
Advanced ADC architectures and their impact on system interrupts.
Power management techniques in microcontroller-based systems.
Key Questions:
What are the trade-offs between clock speed and power consumption in ADC systems?
How does interrupt latency affect real-time system performance?
What are the design considerations for creating an efficient interrupt map in complex IC designs?


SAR는 scaling에 좋아서 요즘은 SAR 많이 쓴다
pipeline은 잘 안쓴다

buffer 만드는게 더 어려워졌따
GHz Buffer는 만들기가 어렵다

RF Receiver MPAC?

Delta-sigma: 그 커다랗던 quantization noise가 loop를 돌아돌아 빠지는 구조다.



Comparator Input TR에 BJT를 쓰면 offset, noise가 적다.
CMOS로 같은 offset, noise 성능을 만들려면 크기를 엄청나게 키워야 한다.


Switched capacitor:
R: no memory, dissipates power
C: memory, does not dissipate power

switched capacitor 구조는 capacitor로 저항을 만드는 방식이다.
switched capacitor, unswitched capacitor를 섞어 RC filter를 만들수도 있다.

switched capacitor 구조의 장점:
C/gm으로 corner frequency가 정해지는 구조랑 다르게,
layout과 design만 잘 되어있다면 switched capacitor 구조에서는 corner frequency가 바뀌지 않는다.
그니까, R, C 모두 C로 구현하면 PVT variation에 적게 영향받는다는 뜻이다.


일반적으로, discrete delta-sigma는 switched capacitor 구조를 쓴다.
continuous delta-sigma는 저항을 쓴다.

continuous delta-sigma에는 RC network를 통해 구성된 oscillator가 있고,
R를 tuning해서 주파수를 맞춰줘야 한다.

Wideband에서는 Continuous 구조가 많이 쓰이는데,
또 continuous 구조에서는 SAR이 많이 쓰인다.

근데, SAR 구조는 comparator를 쓰는데,
comparator는 logic 공정과 함께 scaling되기 아주 쉽다.

다른 analog amp들은 scaling이 어렵다.
scaling을 하면 Rout이 뚝뚝 떨어지는 문제를 겪는다.

그래서 요즘은 wideband, scaled 상황에서는 SAR이 대부분 쓰인다.
미세공정에서 많이 쓰인다는 소리고,
요즘은 SAR로 16bit 이상도 구현해내고 있다.


Delta-Sigma Modulator는 OSR을 필요로 한다.
그래서 Power를 많이 먹는다.
예를 들어 20MHz 출력에 OSR=32면 640MHz 동작을 해야 하는거다.

Pipelined ADC는 OSR 3~5 정도를 쓴다. 딱 2배 fs를 쓰지는 않는다는거다.
앞에서 sharp하게 깎아야 하는데, 너무 sharp하게 깎으면 power가 많이 들기 때문이다?
뭘 sharp하게 깎는건지 확인

Delta sigma에서 OSR을 내리고 싶으면?
Order를 올리면 된다.

Continuous delta-sigma 구조의 장점:
buffer 전류 소비가 상대적으로 적다.

continuous라서 buffer 앞에 저항이 달려있다면 buffer가 signal 주파수에서만 동작하면 되는데,
discrete라서 switched capacitor가 붙어있으면 clock 주파수에서까지 buffer가 동작해야 한다.
그래서 discrete 구조에서는 buffer가 power를 더 먹는다.

또다른 장점:
구조상 continuous에는 RC가 붙는데, 이러면 그 자체로 filtering 효과가 있다.
즉 inherent RC filter가 있는거라, 앞단 filter 차수를 내릴 수 있다.

