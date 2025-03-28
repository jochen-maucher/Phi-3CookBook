# इन्टरएक्टिभ फाइ ३ मिनी ४के इन्स्ट्रक्ट च्याटबट विथ व्हिस्पर

## परिचय

इन्टरएक्टिभ फाइ ३ मिनी ४के इन्स्ट्रक्ट च्याटबट एउटा उपकरण हो जसले प्रयोगकर्ताहरूलाई माइक्रोसफ्ट फाइ ३ मिनी ४के इन्स्ट्रक्ट डेमोमा टेक्स्ट वा अडियो इनपुट मार्फत अन्तरक्रिया गर्न सक्षम बनाउँछ। यस च्याटबटलाई अनुवाद, मौसम जानकारी, र सामान्य जानकारी सङ्कलन जस्ता विभिन्न कार्यहरूको लागि प्रयोग गर्न सकिन्छ।

### सुरु गर्दै

यो च्याटबट प्रयोग गर्न, तलका निर्देशनहरू पालना गर्नुहोस्:

1. नयाँ [E2E_Phi-3-mini-4k-instruct-Whispser_Demo.ipynb](https://github.com/microsoft/Phi-3CookBook/blob/main/code/06.E2E/E2E_Phi-3-mini-4k-instruct-Whispser_Demo.ipynb) खोल्नुहोस्।
2. नोटबुकको मुख्य विन्डोमा, तपाईंलाई टेक्स्ट इनपुट बक्स र "Send" बटन भएको च्याटबक्स इन्टरफेस देखिनेछ।
3. टेक्स्ट-आधारित च्याटबट प्रयोग गर्न, टेक्स्ट इनपुट बक्समा आफ्नो सन्देश टाइप गर्नुहोस् र "Send" बटन क्लिक गर्नुहोस्। च्याटबटले एउटा अडियो फाइल प्रदान गर्नेछ जसलाई नोटबुकभित्रै प्ले गर्न सकिन्छ।

**नोट**: यो उपकरण प्रयोग गर्न GPU र माइक्रोसफ्ट फाइ-३ र OpenAI व्हिस्पर मोडेलहरूको पहुँच आवश्यक पर्छ, जुन स्पिच रिकग्निशन र अनुवादका लागि प्रयोग गरिन्छ।

### GPU आवश्यकताहरू

यो डेमो चलाउन तपाईंसँग १२जीबी GPU मेमोरी हुन आवश्यक छ।

**माइक्रोसफ्ट-फाइ-३-मिनी-४के इन्स्ट्रक्ट** डेमो GPU मा चलाउन आवश्यक मेमोरी इनपुट डेटा (अडियो वा टेक्स्ट), अनुवादको लागि प्रयोग गरिएको भाषा, मोडेलको गति, र GPU मा उपलब्ध मेमोरी जस्ता विभिन्न कारकहरूमा निर्भर गर्दछ।

सामान्यतया, व्हिस्पर मोडेल GPU मा चलाउन डिजाइन गरिएको हो। यो मोडेल चलाउनको लागि सिफारिस गरिएको न्यूनतम GPU मेमोरी ८ जीबी हो, तर आवश्यक परेमा यसले बढी मेमोरी पनि सम्हाल्न सक्छ।

धेरै डेटा चलाउँदा वा मोडेलमा उच्च मात्रा अनुरोध गर्दा बढी GPU मेमोरी आवश्यक पर्न सक्छ वा प्रदर्शन समस्याहरू हुन सक्छ। तपाईंको विशेष आवश्यकताहरूका लागि उपयुक्त सेटिङहरू निर्धारण गर्न विभिन्न कन्फिगरेसनहरूसँग परीक्षण गर्नु र मेमोरी प्रयोगको अनुगमन गर्नु सिफारिस गरिन्छ।

## इन्टरएक्टिभ फाइ ३ मिनी ४के इन्स्ट्रक्ट च्याटबट विथ व्हिस्परको लागि E2E नमुना

[Interactive Phi 3 Mini 4K Instruct Chatbot with Whisper](https://github.com/microsoft/Phi-3CookBook/blob/main/code/06.E2E/E2E_Phi-3-mini-4k-instruct-Whispser_Demo.ipynb) शीर्षक भएको जुपिटर नोटबुकले माइक्रोसफ्ट फाइ ३ मिनी ४के इन्स्ट्रक्ट डेमो प्रयोग गरेर अडियो वा लेखिएको टेक्स्ट इनपुटबाट टेक्स्ट कसरी उत्पन्न गर्ने भनेर देखाउँछ। नोटबुकले केही कार्यहरू परिभाषित गर्दछ:

1. `tts_file_name(text)`: यो कार्यले उत्पन्न गरिएको अडियो फाइल सुरक्षित गर्न इनपुट टेक्स्टको आधारमा फाइल नाम उत्पन्न गर्छ।
2. `edge_free_tts(chunks_list,speed,voice_name,save_path)`: यो कार्यले Edge TTS API प्रयोग गरेर इनपुट टेक्स्टका टुक्राहरूको सूचीबाट अडियो फाइल उत्पन्न गर्छ। इनपुट प्यारामिटरहरूमा टुक्राहरूको सूची, स्पिच दर, भ्वाइस नाम, र उत्पन्न अडियो फाइल सुरक्षित गर्नको लागि आउटपुट पथ समावेश छ।
3. `talk(input_text)`: यो कार्यले Edge TTS API प्रयोग गरेर अडियो फाइल उत्पन्न गर्छ र यसलाई /content/audio डाइरेक्टरीमा र्यान्डम फाइल नाममा सुरक्षित गर्छ। इनपुट प्यारामिटर टेक्स्टलाई स्पिचमा रूपान्तरण गर्न हो।
4. `run_text_prompt(message, chat_history)`: यो कार्यले माइक्रोसफ्ट फाइ ३ मिनी ४के इन्स्ट्रक्ट डेमो प्रयोग गरेर सन्देश इनपुटबाट अडियो फाइल उत्पन्न गर्छ र यसलाई च्याट इतिहासमा थप्छ।
5. `run_audio_prompt(audio, chat_history)`: यो कार्यले व्हिस्पर मोडेल API प्रयोग गरेर अडियो फाइललाई टेक्स्टमा रूपान्तरण गर्छ र यसलाई `run_text_prompt()` कार्यमा पास गर्छ।
6. कोडले ग्राडियो एप लन्च गर्छ जसले प्रयोगकर्ताहरूलाई फाइ ३ मिनी ४के इन्स्ट्रक्ट डेमोमा सन्देश टाइप गरेर वा अडियो फाइल अपलोड गरेर अन्तरक्रिया गर्न अनुमति दिन्छ। आउटपुट एपभित्र टेक्स्ट सन्देशको रूपमा देखाइन्छ।

## समस्या समाधान

Cuda GPU ड्राइभरहरू स्थापना गर्दै

1. सुनिश्चित गर्नुहोस् कि तपाईंको लिनक्स एप्लिकेसनहरू अद्यावधिक छन्।

    ```bash
    sudo apt update
    ```

2. Cuda ड्राइभरहरू स्थापना गर्नुहोस्।

    ```bash
    sudo apt install nvidia-cuda-toolkit
    ```

3. Cuda ड्राइभर स्थान दर्ता गर्नुहोस्।

    ```bash
    echo /usr/lib64-nvidia/ >/etc/ld.so.conf.d/libcuda.conf; ldconfig
    ```

4. Nvidia GPU मेमोरी साइज जाँच गर्दै (१२GB GPU मेमोरी आवश्यक)

    ```bash
    nvidia-smi
    ```

5. क्यास खाली गर्नुहोस्: यदि तपाईं PyTorch प्रयोग गर्दै हुनुहुन्छ भने, torch.cuda.empty_cache() कल गरेर सबै प्रयोग नगरिएका क्यास मेमोरीहरू रिलिज गर्न सक्नुहुन्छ ताकि यसलाई अन्य GPU एप्लिकेसनहरूले प्रयोग गर्न सकून्।

    ```python
    torch.cuda.empty_cache() 
    ```

6. Nvidia Cuda जाँच गर्दै।

    ```bash
    nvcc --version
    ```

7. Hugging Face टोकन बनाउन निम्न कार्यहरू गर्नुहोस्।

    - [Hugging Face Token Settings page](https://huggingface.co/settings/tokens?WT.mc_id=aiml-137032-kinfeylo) मा जानुहोस्।
    - **New token** चयन गर्नुहोस्।
    - प्रयोग गर्न चाहनुभएको प्रोजेक्टको **Name** प्रविष्ट गर्नुहोस्।
    - **Type** लाई **Write** मा चयन गर्नुहोस्।

> **नोट**
>
> यदि तपाईंले निम्न त्रुटि सामना गर्नुभयो भने:
>
> ```bash
> /sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied 
> ```
>
> यसलाई समाधान गर्न, आफ्नो टर्मिनलभित्र निम्न कमाण्ड टाइप गर्नुहोस्।
>
> ```bash
> sudo ldconfig
> ```

**अस्वीकरण**:  
यो दस्तावेज मेसिन-आधारित एआई अनुवाद सेवाहरू प्रयोग गरी अनुवाद गरिएको हो। हामी यथासम्भव शुद्धता सुनिश्चित गर्न प्रयास गर्छौं, तर कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादहरूमा त्रुटि वा असंगतिहरू हुन सक्छन्। यसको मौलिक भाषामा रहेको मूल दस्तावेजलाई प्राधिकृत स्रोत मानिनुपर्छ। महत्त्वपूर्ण जानकारीका लागि, व्यावसायिक मानव अनुवादको सिफारिस गरिन्छ। यो अनुवादको प्रयोगबाट उत्पन्न कुनै पनि गलतफहमी वा गलत व्याख्याको लागि हामी जिम्मेवार हुनेछैनौं।