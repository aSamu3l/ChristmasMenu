# ChristmasMenu

## Description
It is a simple project that uses PHP to generate an HTML site from a JSON file where all the courses of the Christmas lunch/dinner are written so that guests can see the menu directly from their phone.

## How to use

1. **Clone the repository:**
   ```sh
   git clone https://github.com/aSamu3l/ChristmasMenu.git
   cd ChristmasMenu
   ```

2. **Modify the menu:**
   - Open the `menu.json` file in a text editor.
   - Update the menu items as needed. For example:
     ```json
     {
       "appetizer": [
         "Bruschetta",
         "Caprese Salad"
       ],
       "first course": [
         "Spaghetti Carbonara",
         "Gnocchi"
       ],
       "main course": [
         "Florentine Steak",
         "Hunter's Chicken"
       ],
       "dessert": [
         "Ice Cream",
         "Cannoli"
       ]
     }
     ```

3. **Set up a web server:**
   - **Apache:**
     1. Ensure Apache is installed and running.
     2. Place the project directory in the Apache `htdocs` directory (e.g., `/var/www/html/ChristmasMenu`).
     3. Access the project in your browser at `http://localhost/ChristmasMenu`.

   - **Nginx:**
     1. Ensure Nginx is installed and running.
     2. Configure Nginx to serve the project directory. Add a server block in your Nginx configuration:
        ```nginx
        server {
            listen 80;
            server_name localhost;

            root /path/to/ChristmasMenu;
            index index.php index.html;

            location / {
                try_files $uri $uri/ =404;
            }

            location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
            }
        }
        ```
     3. Reload Nginx configuration:
        ```sh
        sudo systemctl reload nginx
        ```
     4. Access the project in your browser at `http://<your-ip>`.

4. **View the Christmas menu:**
   Open your web browser and navigate to the appropriate URL (e.g., `http://<your-ip>/ChristmasMenu` for Apache or `http://<your-ip>` for Nginx) to see the Christmas menu.

## License
This project is distributed under the Apache 2.0 License.