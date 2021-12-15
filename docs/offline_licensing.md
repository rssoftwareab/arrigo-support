# Offline licensing

As part of Arrigo's licensing system (expected to be available q2, 2022) it is possible for Dark Sites (on-premise installations without internet connection) to activate and deactivate their licenses manually.

The outline below explains the procedure to activate and deactivate your licenses.

## Activate license

![image-20211210113334199](./images/activation_process.png)

### 1. Add the license code

Start your license manager on your Arrigo Local computer, select your product and enter your license code then select "Add new key". This should now give you a key in your "Inactive keys".

![image-20211210113334199](./images/add_license_code.png)



### 2. Retrieve the activation certificate

Select the appropriate key in the Inactive keys list. The activation certificate will be displayed in the "Key information" section.

Select "Download" and save the activation certificate on a removable media.

![image-20211210114409754](./images/get_act_certificate.png)



### 3. Generate the license certificate

Go to https://www.activationportal.me/selfservice/activation.aspx?Type=1&cid=7544&pid=9211&lang=en-US  and enter the computers activation certificate in the space provided, then select "Activate". Upon successful generation, a license certificate is generated and can be selected and saved on your removable media.

![image-20211210115742855](./images/generate_license.png)


### 4. Install the license certificate

In the License Manager, select and drag the appropriate license key to the "Active keys" list. A prompt will appear where you can enter your license certificate, then select "Activate".

![image-20211210134752530](./images/install_certificate.png)

Once activated successfully, the license should appear in the "Active keys" list. You can verify the license information by selecting it.

![image-20211210134831843](./images/verify_license.png)


## Deactivate license

![image-20211210113334199](./images/deactivation_process.png)

### 1. Retrieve deactivation certificate

In the License Manager, select and drag the appropriate license key from "Active keys" to "Inactive keys". A prompt will appear where you can select "Deactivate".

![image-20211210134831843](./images/get_deact_certificate.png)

Select "Download" and save the deactivation certificate on a removable media.

![image-20211210134831843](./images/save_deact_certificate.png)

The license is not inactive on the on-premise computer. Please deactivate the license on the license server to free up the license to be used on another machine. If not, the license can still be activated on the current machine by dragging it to "Active keys" and selecting "Activate"

### 2. Deactivate license on license server

Go to https://www.activationportal.me/selfservice/activation.aspx?Type=2&cid=7544&pid=9211&lang=en-US  and enter the computers deactivation certificate in the space provided, then select "Dactivate". Upon successful generation the license is now also deactivated in hte license server and can be used on another machine if required.
