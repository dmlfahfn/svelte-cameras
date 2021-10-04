<script>
    
        export let site = {};
        
    
    </script>
    
    <main>
        <li>{site.title, site.owner}</li>
    </main>
    
    <style>
        main {
            text-align: center;
            padding: 10px;
            max-width: 448px;
            margin: 10px;
            border: 1px solid #ff3e00;
        }
        li {
            list-style: none;
        }
    
        @media (min-width: 640px) {
            main {
                max-width: none;
            }
        }
        
    </style>