### Inspired by [My Smart Home's](https://youtu.be/_aoO5CdymaE?si=VxxMwIuEEPEtWo3Y) Washing Machine card

![Beko HA card - running](https://github.com/salakoayoola/ahssistant/blob/main/images/Cottons%20Rinsing.png?raw=true)
![Beko HA card - OFF](/ahssistant/images/off_beko_remote_control.png)

I tried to recreate the card, specifically for the Beko 742xxxy series

The difference in the tutorial and this specific model are the number of entities.

## To get started:
* Connect the Beko Washing Machine with the HomeWhiz mobile app, you'll have to set up an account for this.
* Integrate HomeWhiz and by extension the washing machine [to HomeAssistant](https://github.com/home-assistant-HomeWhiz/home-assistant-HomeWhiz).
* Be sure to have [button-card](https://github.com/custom-cards/button-card) installed, via HAC.

This specific model has multiple sensor entities, instead of one, necessitating a change in approach.
![Multiple BEKO-HomeWhiz Sensors](/ahssistant/images/binary_sensor.beko_remote_control%20on%20device.png)
* Copy this [YAML](https://github.com/salakoayoola/ahssistant/blob/main/Closet/Washing%20Machine/washing-machine-card.yaml?raw=true) to a Manual Card.
* Replace the sensor entities if your entity names are different. Use Find and Replace All if you have to.
* If you encounter any issues, I refined this code with Google's Gemini and Claude.

HomeWhiz is buggy, very buggy but you'll figure it out. Hopefully, there is a native HACS integration soon, similar to localTuya that'll eliminate the need for cloud dependency.

## Roadmap
* Alert when wash has been completed for a while but the load hasn't been cleared.
>Resource [Home Automation Guy](https://youtu.be/akXurmGJ7oU?si=QJmf7EEOLDPjNyel)
* Telegram Notifications for different stages
* Power Usage Report, weekly or monthly
